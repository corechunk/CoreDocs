# ⚙️ ARM System Control Registers (SCTLR & MPIDR)

## 1. System Control Register (SCTLR_EL1)
Controls top-level EL1 system configurations: enabling MMU address translation, data/instruction caches, and endianness selections.

## 2. Multiprocessor Affinity Register (MPIDR_EL1)
Provides core identification in multi-core SoCs, allowing boot scripts to identify primary CPU core 0 versus secondary cores.
