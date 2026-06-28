# ⚙️ Module 04: RISC-V Architecture

This module details RISC-V register aliases, privilege modes (U/S/M), CSR management, and kernel bootstrapping assembly.

---

## 📄 Core Topics

- [**register-mapping.md**](./register-mapping.md) — Register aliases (`zero`, `ra`, `sp`, `gp`, `tp`, `t0-t6`, `a0-a7`).
- [**privilege-modes.md**](./privilege-modes.md) — U, S, M privilege states and trap vectors.
- [**CSR-management.md**](./CSR-management.md) — Control and Status Registers (mstatus, mie, mtvec, mepc).
- [**boot-bootstrap.md**](./boot-bootstrap.md) — Reset sequences, zeroing BSS, jumping to target C kernels.
