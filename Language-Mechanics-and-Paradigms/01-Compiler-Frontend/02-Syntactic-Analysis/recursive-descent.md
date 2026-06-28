# 🌀 Hand-Written Recursive Descent Parsing

## 1. Top-Down LL Parsing Mechanics
Recursive descent is a top-down parsing technique where each non-terminal grammar rule in an EBNF specification maps directly to a C/C++ or Kotlin function.

```cpp
// Recursive descent parsing routine for expression statements
ASTNode* ParseExpressionStatement() {
    ASTNode* expr = ParseExpression();
    ExpectToken(TOKEN_SEMICOLON);
    return expr;
}
```

## 2. Left Recursion Trap
Top-down parsers enter infinite loops when encountering left-recursive grammar rules (e.g., `Expr ::= Expr '+' Term`). Left recursion must be refactored into iterative loops or right-recursive forms before implementation.
