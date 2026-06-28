# 🧹 Dead Code Elimination (DCE)

## 1. Unreachable Basic Blocks
Identifies and removes CFG basic blocks that can never be executed (e.g., code following an explicit `return` or inside an `if (false)` branch).

## 2. Unused Variable Pruning
Analyzes SSA assignments to strip out calculations whose results are never read by subsequent operations or I/O side effects.
