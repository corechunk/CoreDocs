# 🛠️ Phase 06: Native AOT Compiler Engine

> ### 🛠️ Required Knowledge Depth & Requirements Coverage
> * **Register Allocation Algorithms:** Virtual variable mapping via high-speed Linear Scan allocation or Chaitin-Briggs Graph Coloring, register spilling mechanics & stack slot reservation.
> * **Hardware ABI & Calling Conventions:** System V AMD64 ABI (argument registers `rdi`, `rsi`, `rdx`, etc.), function prologues/epilogues, 16-byte stack frame alignment.
> * **Standalone Binary Generation:** Writing OS object files, constructing ELF headers, program headers, code sections (`.text`, `.data`), symbol tables (`.symtab`), and relocation entries (`.rel.text`).

---

## 🗺️ Module Directory Index

- 🎯 [**01-Register-Allocation-Engine**](./01-Register-Allocation-Engine/README.md) — Mapping virtual variables to CPU registers using Linear Scan allocation or Chaitin-Briggs graph coloring.
- 🏛️ [**02-Target-ABI-Calling-Conventions**](./02-Target-ABI-Calling-Conventions/README.md) — Hardware and OS calling conventions (System V AMD64 ABI), function prologues/epilogues, and stack alignment.
- 📦 [**03-Binary-Object-Generation**](./03-Binary-Object-Generation/README.md) — Constructing standalone ELF executable files, ELF headers, program headers, and symbol relocation tables.
