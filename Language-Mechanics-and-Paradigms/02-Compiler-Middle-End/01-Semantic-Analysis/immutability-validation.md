# 🔒 Immutability Validation and Const Correctness

## 1. Enforcing Immutable Declarations
The semantic pass verifies that variables declared with immutable flags (`val`, `const`, `let`) are assigned exactly once during initialization.

## 2. Reassignment Rejection
Any subsequent assignment expressions targeting an immutable symbol trigger immediate semantic compilation errors.
