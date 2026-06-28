# 🏛️ Language Mechanics and Paradigms Hub

Welcome to the central architectural hub for custom language design, compiler construction, and execution runtimes. This hub bridges high-level formal language specifications with low-level machine code execution across a 7-stage evolution pipeline.

---

## 🗺️ Execution Pipeline & Direct Stage Index

- 📐 [**00-Language-Design-Foundations**](./00-Language-Design-Foundations/README.md) — Formal syntax bounds, EBNF grammar, type systems, scoping, and struct memory layouts.
- 🔍 [**01-Compiler-Frontend**](./01-Compiler-Frontend/README.md) — Lexical analysis (tokenization/DFAs), syntactic parsing (recursive descent/LALR), and AST construction.
- ⚙️ [**02-Compiler-Middle-End**](./02-Compiler-Middle-End/README.md) — Semantic validation, type resolution, Three-Address Code (TAC), SSA form, and IR optimization passes.
- 🐚 [**03-Shell-Execution-Engine**](./03-Shell-Execution-Engine/README.md) — REPL loops, POSIX kernel process primitives (`fork`/`execve`, job control), and stream redirection (`dup2`).
- 🌳 [**04-Interpreter-Runtime-Engine**](./04-Interpreter-Runtime-Engine/README.md) — Dynamic AST tree-walk evaluators, bytecode Virtual Machines (dispatch loops), and managed runtime memory.
- ⚡ [**05-JIT-Compiler-Engine**](./05-JIT-Compiler-Engine/README.md) — Dynamic machine code emission (`mmap PROT_EXEC`), hotspot profiling counters, and runtime trampolines.
- 🛠️ [**06-Native-AOT-Compiler-Engine**](./06-Native-AOT-Compiler-Engine/README.md) — Ahead-Of-Time static compilation, register allocation algorithms, System V AMD64 ABI, and ELF binary emission.
- 🔀 [**07-Hybrid-Unified-Pipeline**](./07-Hybrid-Unified-Pipeline/README.md) — Complete multi-stage engine integration, On-Stack Replacement (OSR), and static binary exporting.
