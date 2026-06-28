# 💻 x86_64 Register Architecture & Execution Modes Reference

This manual details the complete x86_64 register layout, execution modes, control registers, and machine state transitions required for low-level systems programming and OS kernel development.

---

## 1. General Purpose Registers (GPRs) & Bit Aliases

x86_64 provides 16 64-bit general-purpose registers. Each register allows access to smaller 32-bit, 16-bit, and 8-bit sub-sections to preserve backward compatibility.

| 64-bit Register | 32-bit Lower | 16-bit Lower | 8-bit Lower | Legacy Primary Architectural Role |
|---|---|---|---|---|
| `RAX` | `EAX` | `AX` | `AL` | Primary Accumulator (Function return values) |
| `RBX` | `EBX` | `BX` | `BL` | Base Register (Callee-saved data pointer) |
| `RCX` | `ECX` | `CX` | `CL` | Counter Register (Loop counter, Shift counts) |
| `RDX` | `EDX` | `DX` | `DL` | Data Register (I/O port operations, Multiply/Divide) |
| `RSI` | `ESI` | `SI` | `SIL` | Source Index (String operations, 2nd function arg) |
| `RDI` | `EDI` | `DI` | `DIL` | Destination Index (String operations, 1st function arg) |
| `RBP` | `EBP` | `BP` | `BPL` | Base Pointer (Stack frame base anchor) |
| `RSP` | `ESP` | `SP` | `SPL` | Stack Pointer (Current top of hardware stack) |
| `R8` | `R8D` | `R8W` | `R8B` | General Purpose (5th function argument) |
| `R9` | `R9D` | `R9W` | `R9B` | General Purpose (6th function argument) |
| `R10` | `R10D` | `R10W` | `R10B` | General Purpose (Caller-saved temporary, Syscall arg) |
| `R11` | `R11D` | `R11W` | `R11B` | General Purpose (Caller-saved temporary) |
| `R12` | `R12D` | `R12W` | `R12B` | General Purpose (Callee-saved register) |
| `R13` | `R13D` | `R13W` | `R13B` | General Purpose (Callee-saved register) |
| `R14` | `R14D` | `R14W` | `R14B` | General Purpose (Callee-saved register) |
| `R15` | `R15D` | `R15W` | `R15B` | General Purpose (Callee-saved register) |

---

## 2. System Control Registers

Control registers govern CPU operational modes, memory paging, and hardware protections.

| Register | Architectural Name | Key Bit Flags & System Roles |
|---|---|---|
| `CR0` | Control Register 0 | `PE` (Bit 0): Protected Mode Enable.<br>`PG` (Bit 31): Paging Enable.<br>`WP` (Bit 16): Write Protect (enforces read-only page security). |
| `CR2` | Control Register 2 | Page Fault Linear Address (Holds exact memory address that triggered a page fault). |
| `CR3` | Control Register 3 | Page Directory Base Register (Holds physical address of Level 4 Page Table `PML4`). |
| `CR4` | Control Register 4 | `PAE` (Bit 5): Physical Address Extension (Required for Long Mode).<br>`PSE` (Bit 4): Page Size Extension. |
| `EFER` | Extended Feature Enable MSR | `LME` (Bit 8): Long Mode Enable.<br>`LMA` (Bit 10): Long Mode Active (Set by hardware when paging enabled). |

---

## 3. Execution Mode Transitions

An x86 processor transitions through three primary modes during system startup.

```text
+-------------------+       Set CR0.PE = 1       +-------------------+       Set EFER.LME = 1       +-------------------+
|     Real Mode     | ─────────────────────────> |  Protected Mode   | ───────────────────────────> |     Long Mode     |
| (16-bit, 1MB RAM) |                            | (32-bit, 4GB RAM) |       Enable CR0.PG = 1      | (64-bit, 64-bit)  |
+-------------------+                            +-------------------+                              +-------------------+
```

1. **Real Mode (16-bit):** The CPU boots in this legacy mode. Physical memory addressing uses `Segment * 16 + Offset`, restricting total RAM access to 1 Megabyte (`0x00000000` to `0x00100000`).
2. **Protected Mode (32-bit):** Enabled by setting `CR0.PE = 1`. Enables 32-bit flat memory addressing up to 4GB, segment protection rings (Ring 0 to 3), and hardware virtual memory paging.
3. **Long Mode (64-bit):** Enabled by setting `CR4.PAE = 1`, `EFER.LME = 1`, and `CR0.PG = 1`. Provides full 64-bit flat virtual addressing and access to all 16 general-purpose registers.
