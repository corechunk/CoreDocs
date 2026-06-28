# 🔍 Phase 01: Compiler Frontend

> ### 🛠️ Required Knowledge Depth & Requirements Coverage
> * **Lexical & Syntactic Mechanics:** Regular expressions, Deterministic Finite Automata (DFAs), Multi-character lookahead buffers, Hand-written Recursive Descent vs LALR(1) shift-reduce parsing.
> * **Abstract Structure:** Concrete Syntax Trees (CST) vs Abstract Syntax Trees (AST), Visitor/Listener traversal patterns, Panic-mode error recovery resynchronization.
> * **Data Structures Applied:** Queues (Streaming Lexer tokens to Parser), Stacks (Parser call stacks), Trees (AST/CST node hierarchies).

---

## 🗺️ Module Directory Index

- 🔡 [**01-Lexical-Analysis**](./01-Lexical-Analysis/README.md) — Tokenization mechanics, regex matching, DFA state machines, lookahead buffers, and indentation handling.
- 🌲 [**02-Syntactic-Analysis**](./02-Syntactic-Analysis/README.md) — Grammatical parsing models: Recursive descent routines, LALR(1)/LR(k) generators, and lookahead backtracking buffers.
- 🌿 [**03-AST-and-CST-Construction**](./03-AST-and-CST-Construction/README.md) — Building Concrete vs. Abstract Syntax Trees, node class hierarchies, and Visitor pattern traversal algorithms.
- 🚨 [**04-Diagnostics-and-Errors**](./04-Diagnostics-and-Errors/README.md) — Source code location span mapping (line, column, byte offset) and panic-mode resynchronization error handling frameworks.
