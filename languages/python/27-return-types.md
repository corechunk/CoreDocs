# 27 - Return Types (CORE)

Definition: Functions in Python always return a value. If no `return` is specified, the function returns `None`.

## 1. Modern Path (3.12+ / Idiomatic)
Returning multiple values via packing/unpacking.

```python
def get_coords():
    return 10, 20 # Returns a tuple

x, y = get_coords()
print(f"X: {x}, Y: {y}") # Output: X: 10, Y: 20
```

## 2. Systems Path (Internals / C-Interop)
The `return` bytecode operation.

```python
import dis
def dummy(): return 42
dis.dis(dummy)
# Logic: Shows LOAD_CONST and RETURN_VALUE.
```

## 3. Portable Path (Zero-Dependency)
Using `None` as a sentinel for failure.

```python
def find_item(items, target):
    for item in items:
        if item == target:
            return item
    return None
```

## 4. Strict Path (Type-Hinted)
Using `Optional` and `Never`.

```python
from typing import Optional, Never

def safe_divide(a: int, b: int) -> Optional[float]:
    if b == 0: return None
    return a / b

def panic() -> Never:
    raise Exception("Critical Failure")
```

# The Logic Bridge
// Logic: Returning multiple values (e.g., `return a, b`) is syntactically clean in Python because the interpreter automatically "Packs" the values into a single `tuple` object before passing it back to the caller's stack frame.
