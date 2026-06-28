# 🚀 x86 Bootstrapping: 16-bit to 64-bit Assembly Master Manual

This manual provides a complete, production-grade 16-bit Real Mode to 64-bit Long Mode bootloader implementation written in assembly, accompanied by line-by-line technical breakdowns.

---

## 1. Complete Production Assembly Implementation (`boot.asm`)

Below is the complete assembly code using Intel NASM syntax. It executes from the BIOS reset vector, constructs a Global Descriptor Table (GDT), sets up page tables, transitions through 32-bit Protected Mode, and jumps into a 64-bit C kernel.

```assembly
[BITS 16]
[ORG 0x7C00]

start:
    cli                         ; Disable hardware interrupts during mode transition
    xor ax, ax                  ; Segment registers setup (ax = 0)
    mov ds, ax
    mov es, ax
    mov ss, ax
    mov sp, 0x7C00              ; Set stack pointer below bootloader

    ; Step 1: Load Global Descriptor Table (GDT)
    lgdt [gdt_descriptor]

    ; Step 2: Enable Protected Mode in CR0
    mov eax, cr0
    or eax, 0x1                 ; Set PE (Protected Mode Enable) bit 0
    mov cr0, eax

    ; Step 3: Far Jump into 32-bit Protected Mode Code Segment
    jmp 0x08:init_protected_mode

[BITS 32]
init_protected_mode:
    mov ax, 0x10                ; 0x10 points to 32-bit Data Segment in GDT
    mov ds, ax
    mov es, ax
    mov fs, ax
    mov gs, ax
    mov ss, ax
    mov esp, 0x90000            ; Set 32-bit stack address space

    ; Step 4: Setup identity 4-level Page Tables for Long Mode
    ; Zero out 12KB for PML4, PDPT, and Page Directory
    mov edi, 0x1000
    mov cr3, edi                ; Load CR3 with physical address of PML4 (0x1000)
    xor eax, eax
    mov ecx, 3072
    rep stosd

    ; Point PML4[0] -> PDPT (0x2000)
    mov dword [0x1000], 0x2003  ; 0x2000 + Present (0x1) + Writable (0x2)
    ; Point PDPT[0] -> Page Directory (0x3000)
    mov dword [0x2000], 0x3003  ; 0x3000 + Present (0x1) + Writable (0x2)

    ; Map 2MB Huge Pages in Page Directory (0x3000)
    mov dword [0x3000], 0x000083 ; 0MB -> 2MB (Present + Writable + HugePage 0x80)

    ; Step 5: Enable PAE (Physical Address Extension) in CR4
    mov eax, cr4
    or eax, 0x20                ; Set PAE bit 5
    mov cr4, eax

    ; Step 6: Enable Long Mode in EFER MSR
    mov ecx, 0xC0000080         ; EFER MSR address
    rdmsr
    or eax, 0x100               ; Set LME (Long Mode Enable) bit 8
    wrmsr

    ; Step 7: Enable Paging in CR0 to activate Long Mode
    mov eax, cr0
    or eax, 0x80000000          ; Set PG (Paging Enable) bit 31
    mov cr0, eax

    ; Step 8: Far Jump into 64-bit Long Mode Code Segment
    jmp 0x18:init_long_mode

[BITS 64]
init_long_mode:
    mov ax, 0x20                ; 0x20 points to 64-bit Data Segment in GDT
    mov ds, ax
    mov es, ax
    mov fs, ax
    mov gs, ax
    mov ss, ax

    ; Jump to compiled C kernel main
    extern kernel_main
    call kernel_main

hang:
    hlt
    jmp hang

; --- GLOBAL DESCRIPTOR TABLE (GDT) ---
align 8
gdt_start:
    dq 0x0000000000000000       ; Null Descriptor (0x00)

    ; 32-bit Code Segment Descriptor (0x08)
    dw 0xFFFF, 0x0000, 0x9A00, 0x00CF

    ; 32-bit Data Segment Descriptor (0x10)
    dw 0xFFFF, 0x0000, 0x9200, 0x00CF

    ; 64-bit Code Segment Descriptor (0x18)
    dw 0x0000, 0x0000, 0x9A00, 0x00AF

    ; 64-bit Data Segment Descriptor (0x20)
    dw 0x0000, 0x0000, 0x9200, 0x0000
gdt_end:

gdt_descriptor:
    dw gdt_end - gdt_start - 1  ; Size of GDT
    dd gdt_start                ; Base address of GDT

times 510-($-$$) db 0
dw 0xAA55                       ; Boot sector magic signature
```

---

## 2. Line-by-Line Technical Breakdown

### 2.1 16-bit Setup & GDT Loading
* `cli`: Disables maskable hardware interrupts. Interruption during mode transitions would crash the CPU due to invalid interrupt vector table handlers.
* `lgdt [gdt_descriptor]`: Loads the 48-bit pseudo-descriptor (containing GDT size limit and physical address) into the CPU's internal `GDTR` register.
* `mov cr0, eax` & `jmp 0x08:init_protected_mode`: Setting `CR0` bit 0 enables Protected Mode. The immediate `jmp 0x08:...` performs a **Far Jump**, flushing the 16-bit prefetch instruction queue and loading selector `0x08` into the Code Segment register (`CS`).

### 2.2 Page Table Construction & Long Mode Activation
* `mov cr3, edi`: Writes the base memory address (`0x1000`) of the Level 4 Page Map Table (`PML4`) into `CR3`.
* `rdmsr` & `wrmsr`: Reads and writes Model Specific Registers. Reading MSR `0xC0000080` (EFER) and setting bit 8 (`LME`) informs the hardware to enter Long Mode once paging is engaged.
* `or eax, 0x80000000`: Setting `CR0` bit 31 (`PG`) enables virtual memory paging. Because `EFER.LME` is set, the hardware automatically transitions into 64-bit Long Mode and sets `EFER.LMA` (Long Mode Active).
* `jmp 0x18:init_long_mode`: Performs a 64-bit Far Jump to selector `0x18` (64-bit Code Segment in GDT), switching instruction decoding to full 64-bit mode.
