# 📐 Phase 00: Language Design Foundations

> ### 🛠️ Required Knowledge Depth & Requirements Coverage
> * **Language Syntax Boundaries:** Variables (`var`/`val`), Explicit primitive types (`int`, `float`, `string`, `bool`), Control flow (`if`/`else`, `while`/`for`, `return`), Functions & recursion, C-style `struct` containers (excluding vtables/OOP overhead for Base v1.0).
> * **Grammatical & Type Mechanics:** EBNF notation, operator precedence tables, lexical scoping `{ ... }`, nominal vs. structural typing, struct memory padding & alignment.
> * **Data Structures Applied:** Stacks (Shunting-yard operator parsing), Hash Tables (Symbol table scope resolution), Trees (AST node designs).

---

## 🗺️ Module Directory Index

- 🔤 [**01-Lexical-Specification**](./01-Lexical-Specification/README.md) — Rules governing raw source characters, token classification, identifiers, literals, and delimiter strategies.
- 📜 [**02-Formal-Grammar-Syntax**](./02-Formal-Grammar-Syntax/README.md) — Grammatical representations using EBNF, operator associativity, precedence hierarchies, and statement vs. expression semantics.
- 🏷️ [**03-Type-Systems**](./03-Type-Systems/README.md) — Type system architecture: Static vs. dynamic models, strong vs. weak coercion, nominal vs. structural type checking, and Hindley-Milner type inference.
- 🔗 [**04-Scoping-and-Environments**](./04-Scoping-and-Environments/README.md) — Lexical scoping boundaries, dynamic scoping, symbol table stack frames, lifetime tracking, and closure environment capture mechanics.
- 🔀 [**05-Evaluation-and-Control-Flow**](./05-Evaluation-and-Control-Flow/README.md) — Evaluation strategies (eager vs. lazy), parameter passing semantics (value, reference, sharing), primitive branching, and pattern matching.
- 💾 [**06-Memory-Layout-and-Mutability**](./06-Memory-Layout-and-Mutability/README.md) — Stack vs. heap value allocations, binary struct alignment padding, immutability defaults, and ownership move semantics.
