# ⚙️ RISC-V Atomic CSR Manipulation Instructions

This guide details the exact syntax and execution mechanics of RISC-V atomic Control and Status Register (CSR) instructions.

---

## 1. Atomic CSR Instruction Set Syntax

RISC-V provides atomic read-modify-write instructions to inspect and modify CSRs without risk of race conditions or hardware interrupt corruption.

| Assembly Mnemonic | Extended Operand Syntax | Functional Operation Description |
|---|---|---|
| `csrr rd, csr` | `csrrs rd, csr, zero` | **Read CSR:** Reads current CSR value into destination register `rd`. |
| `csrw csr, rs` | `csrrw zero, csr, rs` | **Write CSR:** Overwrites target CSR with value from source register `rs`. |
| `csrs csr, rs` | `csrrs zero, csr, rs` | **Set Bits in CSR:** Performs bitwise OR between CSR and bitmask in `rs`. |
| `csrc csr, rs` | `csrrc zero, csr, rs` | **Clear Bits in CSR:** Performs bitwise AND with inverted bitmask in `rs`. |
| `csrwi csr, imm` | `csrrwi zero, csr, imm` | **Write Immediate:** Overwrites target CSR with 5-bit immediate value `imm`. |
| `csrsi csr, imm` | `csrrsi zero, csr, imm` | **Set Immediate Bits:** Bitwise OR with 5-bit immediate bitmask `imm`. |

---

## 2. Practical Assembly Usage Examples

### 2.1 Enabling Global Hardware Interrupts in M-Mode
```assembly
    ; Enable Machine External Interrupts (MEIE) and Timer Interrupts (MTIE) in mie CSR
    li t0, 0x888                ; Bitmask for MEIE (bit 11) + MTIE (bit 7) + MSIE (bit 3)
    csrs mie, t0                ; Atomically set interrupt bits in mie CSR

    ; Enable Global Interrupts in mstatus CSR
    li t0, 0x8                  ; Bitmask for MIE (Machine Interrupt Enable bit 3)
    csrs mstatus, t0            ; Atomically enable global interrupts
```

### 2.2 Configuring Trap Handler Base Address
```assembly
    la t0, early_trap_handler   ; Load memory address of trap handler routine
    csrw mtvec, t0              ; Atomically write address into Machine Trap Vector CSR
```
