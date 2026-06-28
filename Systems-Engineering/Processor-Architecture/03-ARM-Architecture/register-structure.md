# 📱 ARM64 (AArch64) Register File & Architecture Reference

This manual details the complete ARM64 register file layout, system control registers, and architectural execution states required for bare-metal systems engineering on ARM hardware.

---

## 1. Register Architecture & Sub-Register Mappings

ARM64 provides 31 general-purpose 64-bit registers (`x0` to `x30`). Accessing the lower 32 bits is achieved using `w0` to `w30` aliases.

| 64-bit Register | 32-bit Lower | Standard Procedure Call Standard (AAPCS64) Role | Saved By |
|---|---|---|---|
| `x0` - `x7` | `w0` - `w7` | Parameter registers (Passed to functions) / Return values (`x0-x1`) | Caller |
| `x8` | `w8` | Indirect result location register | Caller |
| `x9` - `x15` | `w9` - `w15` | Temporary registers (Scratchpad memory) | Caller |
| `x16` - `x17` | `w16` - `w17` | Intra-procedure call scratch registers (Used by linkers/veneers) | Caller |
| `x18` | `w18` | Platform Register (Reserved for OS kernels/runtimes) | Platform |
| `x19` - `x28` | `w19` - `w28` | Callee-saved registers (Preserved across function calls) | Callee |
| `x29` | `w29` | Frame Pointer (`FP`) - Anchors stack frames | Callee |
| `x30` | `w30` | Link Register (`LR`) - Holds subroutine return address | Callee |
| `SP` | `WSP` | Stack Pointer (Must maintain 16-byte alignment) | System |
| `XZR` | `WZR` | Zero Register (Reads constant 0, discards writes) | Hardware |

---

## 2. System Control & State Registers

System registers in ARM64 are accessed using `mrs` (Move System Register to General Register) and `msr` (Move General Register to System Register).

| System Register | Full Architectural Name | Function & System Role |
|---|---|---|
| `SCTLR_EL1` | System Control Register (EL1) | Controls MMU enable (`M` bit 0), instruction/data caches (`I`/`C` bits), and alignment fault checks. |
| `MPIDR_EL1` | Multiprocessor Affinity Register | Identifies individual CPU core IDs in multi-core SoCs (`Aff0` field returns core index). |
| `CurrentEL` | Current Exception Level | Holds the current execution privilege level (Bits [3:2] return 0, 1, 2, or 3). |
| `VBAR_EL1` | Vector Base Address Register | Holds base memory address of the EL1 exception vector table. |
| `DAIF` | Interrupt Mask Bits | Controls masking of Debug (`D`), SError (`A`), IRQ (`I`), and FIQ (`F`) interrupts. |

---

## 3. Exception Level Privilege Hierarchy

ARM64 enforces hardware isolation through 4 discrete Exception Levels (`EL0` to `EL3`).

```text
+-------------------------------------------------------------------+
|      EL3: Secure Monitor / Firmware (TrustZone, ATF Boot)         |
+-------------------------------------------------------------------+
                                  │
                                  ▼
+-------------------------------------------------------------------+
|      EL2: Hypervisor (KVM, Xen Virtualization Engine)             |
+-------------------------------------------------------------------+
                                  │
                                  ▼
+-------------------------------------------------------------------+
|      EL1: Operating System Kernel (Linux, FreeBSD Kernel)         |
+-------------------------------------------------------------------+
                                  │
                                  ▼
+-------------------------------------------------------------------+
|      EL0: Unprivileged Applications (User Apps, Shells)            |
+-------------------------------------------------------------------+
```
