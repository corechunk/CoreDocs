# 🔒 Mutability Semantics and Ownership

## 1. Mutability Flags
- Immutability by default (`val` or `const`) prevents unexpected state mutation across concurrent threads.
- Explicit mutability (`var` or `mut`) signals state transformations.

## 2. Move Semantics
Transferring ownership of a heap resource invalidates the original reference variable, eliminating double-free memory corruption.
