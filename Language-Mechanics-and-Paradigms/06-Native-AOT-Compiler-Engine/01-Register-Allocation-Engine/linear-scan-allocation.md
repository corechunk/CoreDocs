# ⚡ High-Speed Linear Scan Register Allocation

## 1. Live Range Analysis
Linear scan computes continuous live intervals for every virtual variable across basic blocks from their first assignment to their last read.

## 2. Linear Scan Algorithm
Processes live intervals sorted by start point, assigning available physical CPU registers (e.g., `rax`, `rcx`, `r8-r15`). Linear scan operates in $O(N)$ time, making it ideal for fast JIT or debug builds.
