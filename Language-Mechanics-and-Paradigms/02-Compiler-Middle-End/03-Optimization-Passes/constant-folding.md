# 🔢 Compile-Time Constant Folding and Propagation

## 1. Constant Folding
Replaces constant expressions with their pre-calculated results at compile time (e.g., rewriting `3 + 5 * 2` directly to `13` in IR).

## 2. Constant Propagation
Replaces variable references with known constant values across basic blocks, enabling further downstream optimizations.
