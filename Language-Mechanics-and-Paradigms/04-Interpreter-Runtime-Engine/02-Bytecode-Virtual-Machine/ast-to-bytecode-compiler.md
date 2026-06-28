# 🔲 Compiling AST Structures to Bytecode Opcodes

## 1. Bytecode Emission
Bytecode Virtual Machines convert tree ASTs into flat arrays of 1-byte instruction opcodes (e.g., `OP_ADD`, `OP_LOAD_CONST`, `OP_JUMP_IF_FALSE`) paired with constant pool operands.

## 2. Stack-Based VM Architecture
Operands are pushed onto and popped off an internal VM evaluation stack:

```text
OP_LOAD_CONST 0  // Push constant 10 onto VM stack
OP_LOAD_CONST 1  // Push constant 20 onto VM stack
OP_ADD           // Pop both, add, push result (30)
```
