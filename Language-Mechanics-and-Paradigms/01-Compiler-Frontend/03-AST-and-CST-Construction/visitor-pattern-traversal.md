# 🚶 Visitor Pattern Traversal Mechanisms

## 1. Decoupling Operations from Tree Structures
Instead of polluting AST node classes with compiler passes (type checking, code generation, optimization), compilers utilize the **Visitor Design Pattern**.

## 2. Double Dispatch Execution Loop
Each AST node implements an `Accept(Visitor* v)` method, which dispatches back to the specific `VisitBinaryExpr`, `VisitIfStmt`, or `VisitVarDecl` overload on the active compiler pass object.
