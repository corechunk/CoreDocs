# 📑 Concrete Syntax Trees (Parse Trees)

## 1. Concrete Syntax Trees (CST) vs. AST
While an AST strips out non-semantic syntax, a Concrete Syntax Tree (CST) preserves 100% full fidelity of the input character stream—including comments, whitespace, explicit semicolons, and grouping parentheses.

## 2. Industry Use Cases
CSTs are essential for IDE tooling, automated code formatters (e.g., Prettier, `clang-format`), refactoring tools, and static analysis linters that must rewrite code without losing original formatting.
