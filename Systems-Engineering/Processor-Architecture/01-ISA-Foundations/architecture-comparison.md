# ⚖️ Architecture Comparison: CISC vs. RISC

## 1. CISC (Complex Instruction Set Computer - x86)
- Uses variable-length instructions and microcode translation layers.
- Supports memory-to-register arithmetic operations directly.

## 2. RISC (Reduced Instruction Set Computer - ARM, RISC-V)
- Uses fixed-length instructions and prioritized power efficiency.
- Strictly adheres to a **Load-Store Architecture**: arithmetic operations occur strictly within CPU registers; memory access requires explicit `load` and `store` instructions.
