# 09 - Data Types (CORE - Hub)

Definition: In Python, "Everything is an Object." There are no primitive types at the source level. Every value is an instance of a class, inheriting from `object`.

## Type System Overview

| Category | Type | Hub Link |
| :--- | :--- | :--- |
| **Integers** | `int` | [integers.md](./data-type/integers.md) |
| **Floating Point** | `float` | [floats.md](./data-type/floats.md) |
| **Booleans** | `bool` | [booleans.md](./data-type/booleans.md) |
| **Strings** | `str` | [10-string-escaping.md](./10-string-escaping.md) |
| **Special** | `NoneType` | [none-type.md](none-type.md) |

## 1. Modern Path (3.12+ / Idiomatic)
Checking types using the modern `isinstance` and `type` mechanisms.

```python
x = 42
print(type(x)) # Output: <class 'int'>
print(isinstance(x, int)) # Output: True
```

## 2. Systems Path (Internals / C-Interop)
Examining the `PyObject` header through size checks.

```python
import sys

# Integers are arbitrary precision in Python
huge_num = 10**100
print(f"Size of huge_num: {sys.getsizeof(huge_num)} bytes")
# Output: Size of huge_num: 72 bytes
```

## 3. Portable Path (Zero-Dependency)
Basic type usage in standard logic.

```python
is_active = True
data = None
print(f"State: {is_active}, Data: {data}") # Output: State: True, Data: None
```

## 4. Strict Path (Type-Hinted)
Explicitly defining expected types in data models.

```python
from typing import Union

# Variable can be Int or Float
score: Union[int, float] = 95.5
name: str = "Python"

print(f"{name}: {score}") # Output: Python: 95.5
```

# The Logic Bridge
// Logic: Since everything is an object, even a simple integer has the overhead of a reference count and a type pointer. Python's `int` is unique because it is "arbitrary-precision," meaning it automatically allocates more memory to prevent overflow, unlike the fixed-width integers in C or Kotlin.
