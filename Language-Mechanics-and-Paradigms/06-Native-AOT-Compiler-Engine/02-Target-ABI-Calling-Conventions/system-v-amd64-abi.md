# 🏛️ System V AMD64 ABI Specifications

## 1. Argument Register Mapping (Linux / macOS)
The System V AMD64 ABI dictates passing the first 6 integer/pointer arguments in specific hardware registers:
1. `rdi`, 2. `rsi`, 3. `rdx`, 4. `rcx`, 5. `r8`, 6. `r9`

Additional parameters are pushed right-to-left onto the stack.

## 2. Return Values & Scratch Registers
- Return values are placed inside `rax` (and `rdx` for 128-bit values).
- Caller-saved (scratch) registers: `rax`, `rcx`, `rdx`, `rsi`, `rdi`, `r8-r11`.
- Callee-saved (preserved) registers: `rbx`, `rsp`, `rbp`, `r12-r15`.
