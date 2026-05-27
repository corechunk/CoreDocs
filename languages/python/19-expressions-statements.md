# 19 - Expressions & Statements (CORE)

Definition: Statements perform actions; expressions evaluate to values. Python is a statement-heavy language, but recent versions have added expression power (e.g., Walrus operator).

## 1. Modern Path (3.12+ / Idiomatic)
The Walrus Operator (`:=`) as an assignment expression.

```python
if (n := len([1, 2])) > 0:
    print(f"Length: {n}") # Output: Length: 2
```

## 2. Systems Path (Internals / C-Interop)
Bytecode difference between statements and expressions.

```python
import dis
dis.dis("x = 1")   # STORE_NAME
dis.dis("x == 1")  # COMPARE_OP
```

## 3. Portable Path (Zero-Dependency)
Standard conditional expression (Ternary).

```python
status = "OK" if True else "ERR"
```

## 4. Strict Path (Type-Hinted)
Annotated statements.

```python
name: str = "Core" # Annotated assignment statement
```

# The Logic Bridge
// Logic: The Walrus operator allowed Python to break the "Assignment is always a statement" rule. Under the hood, it performs a standard `STORE_NAME` but leaves the value on the stack for the next instruction, allowing it to be used inside conditionals.
