# ⚡ Function Inlining, Loop Unrolling, and Vectorization

## 1. Function Inlining Heuristics
Replaces small function call sites directly with the function's body code, eliminating function call overhead (prologues/epilogues and branch jumps).

## 2. Loop Transformations
- **Loop Unrolling:** Replicates loop bodies to reduce loop control branching checks.
- **Auto-Vectorization:** Packs independent scalar operations inside loops into Single Instruction, Multiple Data (SIMD) hardware vector instructions.
