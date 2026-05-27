# 21 - Type Casting (CORE)

Definition: Converting a value from one type to another. Python uses constructor functions for explicit casting.

## 1. Modern Path (3.12+ / Idiomatic)
Safe casting with `try-except`.

```python
s = "42"
try:
    val = int(s)
except ValueError:
    val = 0
```

## 2. Systems Path (Internals / C-Interop)
C-style casting using `ctypes`.

```python
import ctypes
x = 10
# Casting to a C integer pointer
ptr = ctypes.cast(id(x), ctypes.POINTER(ctypes.c_int))
```

## 3. Portable Path (Zero-Dependency)
Standard casting functions.

```python
print(float(10)) # 10.0
print(str(100))  # "100"
```

## 4. Strict Path (Type-Hinted)
Using `cast` from the `typing` module (Static only).

```python
from typing import Any, cast
val: Any = 10
num = cast(int, val) # Tells mypy it's an int
```

# The Logic Bridge
// Logic: Functions like `int()` or `str()` are actually class constructors. When called, they create a new object of the target type. `typing.cast` is a "No-Op" at runtime; it exists solely for the static type checker and is ignored by the interpreter.
