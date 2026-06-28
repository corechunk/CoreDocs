# 🌳 Recursive AST Node Evaluation

## 1. Direct Tree-Walk Evaluation Mechanics
A tree-walk interpreter evaluates source programs by executing a recursive traversal over the AST (via the Visitor pattern or polymorphic `Evaluate()` methods), computing results directly on syntax nodes.

```cpp
// Evaluating binary expressions recursively
Value EvaluateBinaryExpr(BinaryExpr* node, Environment* env) {
    Value left = Evaluate(node->left, env);
    Value right = Evaluate(node->right, env);
    if (node->op == ADD) return AddValues(left, right);
    // ...
}
```

## 2. Dynamic Performance Overhead
Tree-walk interpreters suffer from pointer-chasing and CPU cache misses due to fragmented memory allocations across deep AST node trees.
