# 🔍 Identifier Symbol Resolution Across Scope Bounds

## 1. Symbol Table Binding
Semantic analyzer passes bind AST variable and function identifier nodes to their exact definitions stored inside scope symbol tables.

## 2. Unbound Symbol & Shadowing Validation
- Flags references to undeclared variables as compile-time errors.
- Enforces shadowing rules when local scope variables declare identical names to outer scope symbols.
