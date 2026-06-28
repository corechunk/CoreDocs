# 🚀 ARM64 (AArch64) Multi-Core Bootstrapping Master Manual

This manual provides a complete, production-grade ARM64 bare-metal initialization script written in AArch64 assembly, demonstrating EL3 to EL1 exception level drops, multi-core sleep traps, and jumping into a C kernel.

---

## 1. Complete Production Assembly Implementation (`boot.S`)

```assembly
.section .text.boot
.global _start

_start:
    ; Step 1: Read Multi-Core ID from MPIDR_EL1
    mrs x0, mpidr_el1
    and x0, x0, #0xFF           ; Extract Aff0 (Core ID)
    cbz x0, primary_core        ; If Core 0, branch to initialization

secondary_core:
    ; Secondary cores (Core 1, 2, 3...) trap here in low-power sleep loop
    wfe                         ; Wait For Event
    b secondary_core

primary_core:
    ; Step 2: Check current Exception Level (CurrentEL)
    mrs x0, CurrentEL
    lsr x0, x0, #2
    cmp x0, #3
    b.ne drop_to_el1            ; If not EL3, skip EL3 setup

setup_el3:
    ; Configure EL3 system control registers
    mov x0, #0x5b1              ; RES1 bits + RW=1 (AArch64 EL2) + NS=1 (Non-secure)
    msr scr_el3, x0
    mov x0, #0x3c9              ; DAIF masked + EL1h mode
    msr spsr_el3, x0
    adr x0, setup_el1
    msr elr_el3, x0
    eret                        ; Return from EL3 -> jumps to setup_el1 in EL1

drop_to_el1:
setup_el1:
    ; Step 3: Disable MMU and Caches initially in SCTLR_EL1
    mrs x0, sctlr_el1
    bic x0, x0, #(1 << 0)       ; Clear M bit (Disable MMU)
    bic x0, x0, #(1 << 2)       ; Clear C bit (Disable Data Cache)
    bic x0, x0, #(1 << 12)      ; Clear I bit (Disable Instruction Cache)
    msr sctlr_el1, x0

    ; Step 4: Setup Stack Pointer for EL1 (SP_EL1)
    adr x0, _stack_top
    mov sp, x0

    ; Step 5: Zero out .bss memory section
    adr x0, _bss_start
    adr x1, _bss_end
zero_bss_loop:
    cmp x0, x1
    b.ge jump_to_kernel
    str xzr, [x0], #8           ; Store zero register and increment pointer by 8
    b zero_bss_loop

jump_to_kernel:
    ; Step 6: Jump to C Kernel main
    bl kernel_main

dead_loop:
    wfi                         ; Wait for Interrupt (Halt core)
    b dead_loop
```

---

## 2. Line-by-Line Technical Breakdown

### 2.1 Multi-Core Core Identification & Sleep Traps
* `mrs x0, mpidr_el1` & `and x0, x0, #0xFF`: Reads the Multiprocessor Affinity Register. Masking with `0xFF` isolates `Aff0`, returning `0` for the primary CPU core and `1, 2, 3...` for secondary cores.
* `wfe`: Executes **Wait For Event**. Secondary cores enter an architectural low-power standby state, saving battery and thermal headroom until primary core 0 sends an Event signal (via `sev` instruction) to wake them up.

### 2.2 Exception Level Drop (`ERET` Execution)
* `msr scr_el3, x0`: Writes to Secure Configuration Register 3, setting `RW=1` (Execution in EL2/EL1 is 64-bit AArch64) and `NS=1` (Non-Secure state).
* `msr spsr_el3, x0` & `msr elr_el3, x0`: Prepares Saved Program Status Register and Exception Link Register. `spsr_el3` is configured with `0x3c9` (`EL1h` stack mode with interrupts masked). `elr_el3` is loaded with the memory address of `setup_el1`.
* `eret`: Executes **Exception Return**. The CPU atomically switches hardware state to EL1 and branches execution directly to `setup_el1`.

### 2.3 Stack & Memory Initialization
* `str xzr, [x0], #8`: Utilizes ARM64 post-indexed addressing. Stores 64-bits of zeroes from the hardware Zero Register (`xzr`) into memory address `x0`, then automatically increments `x0` by 8 bytes.
