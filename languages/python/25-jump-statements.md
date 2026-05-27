# 25 - Jump Statements (PRO)

Definition: Altering control flow via `break`, `continue`, and `return`. Python does not have `goto`.

## 1. Modern Path (3.12+ / Idiomatic)
Using `break` in a loop-else construct (Unique to Python).

```python
for i in range(5):
    if i == 10: break
else:
    print("Loop finished without break") # Output: Loop finished...
```

## 2. Systems Path (Internals / C-Interop)
The `BREAK_LOOP` (legacy) or `JUMP_FORWARD` bytecode.

```python
import dis
dis.dis("while True: break")
```

## 3. Portable Path (Zero-Dependency)
Basic `continue`.

```python
for i in range(3):
    if i == 1: continue
    print(i) # Output: 0 2
```

## 4. Strict Path (Type-Hinted)
Function returns as jump points.

```python
def check(val: int) -> bool:
    if val < 0: return False
    return True
```

# The Logic Bridge
// Logic: The `else` block after a loop is a unique Python feature—it executes only if the loop terminates normally (without hitting a `break`). This is ideal for search logic where you want to perform an action if a target was not found.
