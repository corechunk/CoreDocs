# 🌳 AST Node Class Hierarchies

## 1. Abstract Syntax Trees (AST)
An AST represents the structural logic of source code, omitting syntactic noise like parentheses, braces, and commas.

## 2. Polymorphic Node Categories
AST nodes are organized into class hierarchies based on program roles:
- **Expression Nodes:** Evaluate to values (`BinaryExpr`, `LiteralExpr`, `VariableExpr`).
- **Statement Nodes:** Represent execution actions (`IfStmt`, `WhileStmt`, `ReturnStmt`).
- **Declaration Nodes:** Define symbols in symbol tables (`VarDecl`, `FuncDecl`, `StructDecl`).
