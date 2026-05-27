# 18 - Precedence & Associativity (CORE)

Definition: Rules determining the order of operator evaluation.

## 1. Modern Path (3.12+ / Idiomatic)
Using parentheses for clarity in complex expressions.

```python
res = (10 + 2) * 5 # 60
```

## 2. Systems Path (Internals / C-Interop)
Viewing the expression tree via the `ast` module.

```python
import ast
tree = ast.parse("1 + 2 * 3")
# Logic: Shows Multiply node nested deeper than Add node.
```

## 3. Portable Path (Zero-Dependency)
Standard PEMDAS order.

```python
res = 10 + 2 * 3 # 16
```

## 4. Strict Path (Type-Hinted)
Explicit typing for intermediate results.

```python
a: int = 10
b: int = 5
c: float = (a + b) / 2
```

# The Logic Bridge
// Logic: Python follows C precedence rules. Power (`**`) has the highest priority, followed by unary operators, then multiplication/division, and finally addition/subtraction. Logical `and` is evaluated before `or`.
