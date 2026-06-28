# ⚙️ RISC-V (RV64I) Register File & Architecture Reference

This manual details the complete RISC-V RV64I register file layout, ABI mnemonic aliases, and Control and Status Registers (CSRs) required for low-level systems engineering.

---

## 1. Register Architecture & Standard ABI Mnemonic Mapping

RISC-V provides 32 general-purpose 64-bit registers (`x0` to `x31`). In assembly programming, developers use standardized ABI mnemonic names rather than raw `x` numbers.

| Register Number | Standard ABI Mnemonic | Architectural Description | Saver (Calling Convention) |
|---|---|---|---|
| `x0` | `zero` | Hardwired Constant Zero (Discards all writes) | N/A |
| `x1` | `ra` | Return Address (Saved by `jal`/`jalr` instructions) | Caller |
| `x2` | `sp` | Stack Pointer (Top of active hardware stack frame) | Callee |
| `x3` | `gp` | Global Pointer (Points to static global data base) | Global |
| `x4` | `tp` | Thread Pointer (Points to thread-local storage TLS) | Thread |
| `x5` - `x7` | `t0` - `t2` | Temporary Registers (Scratchpad memory) | Caller |
| `x8` | `s0` / `fp` | Saved Register / Frame Pointer | Callee |
| `x9` | `s1` | Saved Register | Callee |
| `x10` - `x11` | `a0` - `a1` | Function Arguments / Return Values | Caller |
| `x12` - `x17` | `a2` - `a7` | Function Arguments | Caller |
| `x18` - `x27` | `s2` - `s11` | Saved Registers (Preserved across function calls) | Callee |
| `x28` - `x31` | `t3` - `t6` | Temporary Registers | Caller |
| `pc` | `pc` | Program Counter (Holds current instruction memory address) | System |

---

## 2. Control and Status Registers (CSRs)

RISC-V separates hardware system control into dedicated Control and Status Registers accessed via specialized atomic instructions (`csrr`, `csrw`, `csrs`, `csrc`).

| CSR Name | Privilege Level | Architectural Function & System Role |
|---|---|---|
| `mstatus` | Machine (M-Mode) | Machine Status Register. Tracks hardware interrupt enables (`MIE`), previous interrupt states (`MPIE`), and previous privilege mode (`MPP`). |
| `misa` | Machine (M-Mode) | Machine Instruction Set Architecture. Reports supported ISA extensions (e.g., `I`, `M`, `A`, `F`, `D`, `C`). |
| `mie` / `mip` | Machine (M-Mode) | Machine Interrupt Enable / Machine Interrupt Pending registers. |
| `mtvec` | Machine (M-Mode) | Machine Trap-Vector Base Address Register. Points to trap handler memory entry address. |
| `mepc` | Machine (M-Mode) | Machine Exception Program Counter. Holds return address when returning from an M-mode trap via `mret`. |
| `medeleg` / `mideleg` | Machine (M-Mode) | Machine Exception/Interrupt Delegation Registers. Configures which traps bypass M-mode and delegate directly to S-mode. |
| `satp` | Supervisor (S-Mode) | Supervisor Address Translation and Protection. Holds physical page table base address (Equivalent to x86 `CR3`). |

---

## 3. Privilege Modes Hierarchy

RISC-V defines three standard hardware privilege modes.

```text
+-------------------------------------------------------------------+
|      M-Mode: Machine Mode (Highest privilege, OpenSBI Firmware)   |
+-------------------------------------------------------------------+
                                  │ (Delegates traps via mideleg)
                                  ▼
+-------------------------------------------------------------------+
|      S-Mode: Supervisor Mode (OS Kernel, Linux Virtual Memory)    |
+-------------------------------------------------------------------+
                                  │ (Executes ecall)
                                  ▼
+-------------------------------------------------------------------+
|      U-Mode: User Mode (Unprivileged Application Binaries)         |
+-------------------------------------------------------------------+
```
