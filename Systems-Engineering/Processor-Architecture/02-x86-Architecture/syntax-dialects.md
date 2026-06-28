# 🔀 x86 Syntax Dialects: Intel vs. AT&T

## 1. Syntax Comparison Matrix

| Feature Metric | Intel Syntax (NASM / MASM) | AT&T Syntax (GNU `as` / GCC) |
|---|---|---|
| **Operand Order** | `instruction destination, source` | `instruction source, destination` |
| **Example** | `mov rax, rbx` | `movq %rbx, %rax` |
| **Register Prefix** | None (`rax`) | `%` prefix (`%rax`) |
| **Immediate Prefix** | None (`42`) | `$` prefix (`$42`) |
| **Instruction Suffix** | Explicit size directives (`dword ptr`) | Size suffixes (`b`, `w`, `l`, `q`) |
