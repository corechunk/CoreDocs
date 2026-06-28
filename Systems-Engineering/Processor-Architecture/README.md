# 🖥️ Processor Architecture Sub-Hub

Welcome to the silicon hardware internals sub-hub. This hub details ISA foundations, hardware privilege levels, register layouts, and boot assembly sequences across x86, ARM, and RISC-V architectures.

---

## 🗺️ Direct Hardware Module Index

- 📐 [**01-ISA-Foundations**](./01-ISA-Foundations/README.md) — Unified concepts, assembly introduction, hardware privilege modes, and CISC vs. RISC comparisons.
- 💻 [**02-x86-Architecture**](./02-x86-Architecture/README.md) — Real to Long mode transitions, memory segmentation (GDT/LDT), Intel vs. AT&T syntax, and 16-to-64-bit bootloader assembly.
- 📱 [**03-ARM-Architecture**](./03-ARM-Architecture/README.md) — AArch64 register files, Exception Levels (EL0-EL3), SCTLR/MPIDR control registers, and multi-core sleep traps.
- ⚙️ [**04-RISC-V-Architecture**](./04-RISC-V-Architecture/README.md) — Register aliases (`zero`, `ra`, `sp`, `a0-a7`), U/S/M privilege modes, CSR management, and kernel bootstrap assembly.
