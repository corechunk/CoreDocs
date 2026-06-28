# 📝 Three-Address Code (TAC) Instructions

## 1. Target-Agnostic Linear IR
Three-Address Code (TAC) linearizes nested AST structures into flat instruction sequences where each instruction has at most three operands.

```text
t1 = a * b
t2 = c + t1
x = t2
```

## 2. Quads vs. Triples
- **Quads:** Represented as explicit record tuples `(operator, operand1, operand2, result)`.
- **Triples:** Avoid explicit result names by referencing instruction array indices directly.
