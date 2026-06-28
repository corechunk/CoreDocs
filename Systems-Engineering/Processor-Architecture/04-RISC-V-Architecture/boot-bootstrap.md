# 🚀 RISC-V Bootstrapping: M-Mode to S-Mode Assembly Master Manual

This manual provides a complete, production-grade RISC-V RV64I bare-metal initialization script written in assembly, demonstrating M-mode power-on execution, trap delegation to S-mode, memory BSS zeroing, and executing `mret` to launch a C kernel.

---

## 1. Complete Production Assembly Implementation (`boot.s`)

```assembly
.section .text.init
.global _start

_start:
    ; Step 1: Disable global interrupts in M-Mode
    csrc mstatus, 0x8           ; Clear MIE (bit 3) in mstatus CSR

    ; Step 2: Set up Machine Trap Vector
    la t0, early_m_trap_handler
    csrw mtvec, t0

    ; Step 3: Delegate interrupts and exceptions to S-Mode
    li t0, 0xffff               ; Delegate all exceptions
    csrw medeleg, t0
    li t0, 0xffff               ; Delegate all interrupts
    csrw mideleg, t0

    ; Step 4: Setup Stack Pointer for Supervisor Mode (sp)
    la sp, _stack_top

    ; Step 5: Zero out .bss memory section
    la t0, _bss_start
    la t1, _bss_end
zero_bss_loop:
    bge t0, t1, prepare_s_mode
    sd zero, 0(t0)              ; Store double-word (8 bytes) of zeroes
    addi t0, t0, 8
    j zero_bss_loop

prepare_s_mode:
    ; Step 6: Configure Previous Privilege Mode (MPP) in mstatus to Supervisor (0x1)
    csrr t0, mstatus
    li t1, ~(3 << 11)           ; Mask out MPP bits [12:11]
    and t0, t0, t1
    li t1, (1 << 11)            ; 1 = Supervisor Mode (S-Mode)
    or t0, t0, t1
    csrw mstatus, t0

    ; Step 7: Load C Kernel main address into mepc CSR
    la t0, kernel_main
    csrw mepc, t0

    ; Step 8: Return from M-Mode to S-Mode -> Executes kernel_main
    mret

early_m_trap_handler:
    ; Fallback M-mode trap handler
    wfi
    j early_m_trap_handler
```

---

## 2. Line-by-Line Technical Breakdown

### 2.1 Interrupt Disabling & Trap Delegation
* `csrc mstatus, 0x8`: Uses **Clear Bits in CSR**. Atomically clears bit 3 (`MIE`) in the Machine Status register to prevent hardware timer or external interrupts from firing during early boot setup.
* `csrw medeleg, t0` & `csrw mideleg, t0`: Writes to Machine Exception and Interrupt Delegation registers. Setting bits in these CSRs instructs the CPU hardware to route exceptions (like page faults or system calls) directly to Supervisor Mode (`stvec`) rather than trapping into Machine Mode (`mtvec`).

### 2.2 Memory Initialization
* `sd zero, 0(t0)` & `addi t0, t0, 8`: Uses RISC-V 64-bit store (`sd`). Writes 8 bytes of zeroes from the hardwired `zero` register into memory location `t0`, then increments `t0` by 8 bytes until the entire `.bss` uninitialized variable space is cleared.

### 2.3 Privilege Drop (`MRET` Execution)
* `li t1, ~(3 << 11)` & `or t0, t0, t1`: Manipulates the `MPP` (Machine Previous Privilege) field in `mstatus` (bits [12:11]). Setting `MPP = 01` configures the CPU hardware to drop to Supervisor Mode upon returning from Machine Mode.
* `csrw mepc, t0`: Loads the memory entry address of the C kernel's `kernel_main` function into the Machine Exception Program Counter (`mepc`).
* `mret`: Executes **Machine Environment Return**. The hardware atomically sets the current privilege mode to S-Mode (from `mstatus.MPP`), re-enables interrupts (restoring `MIE` from `MPIE`), and sets the Program Counter (`pc`) to the address held in `mepc`, launching the C kernel.
