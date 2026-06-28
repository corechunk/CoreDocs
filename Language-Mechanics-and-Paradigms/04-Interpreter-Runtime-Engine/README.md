# 🌳 Phase 04: Interpreter Runtime Engine

> ### 🛠️ Required Knowledge Depth & Requirements Coverage
> * **Dynamic Evaluation Engines:** Recursive AST tree-walk evaluation, dynamic runtime evaluation stack frames, symbol table environment chaining.
> * **Virtual Machine Construction:** Compiling AST to compact bytecode opcodes, Opcode dispatch loops (switch-dispatch vs direct-threaded code).
> * **Managed Runtime Memory:** Dynamic heap allocations, managed struct memory layouts, Automatic Reference Counting (ARC) vs tracing Mark-and-Sweep Garbage Collection.

---

## 🗺️ Module Directory Index

- 🚶 [**01-AST-Tree-Walk-Evaluator**](./01-AST-Tree-Walk-Evaluator/README.md) — Direct recursive AST node evaluation engines and dynamic runtime stack frame environments.
- 🔲 [**02-Bytecode-Virtual-Machine**](./02-Bytecode-Virtual-Machine/README.md) — Compiling AST to bytecode opcodes, stack-based VM loops, and opcode dispatch optimizations.
- 🧹 [**03-Memory-Management-Runtime**](./03-Memory-Management-Runtime/README.md) — Stack vs. heap allocations, managed memory boundaries, ARC reference counting, and Mark-and-Sweep Garbage Collection.
