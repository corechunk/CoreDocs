# None Type (CORE)

Definition: `None` is a special constant representing the absence of a value or a null state.

## 1. Modern Path (3.12+ / Idiomatic)
Identity comparison using `is`.

```python
val = None
if val is None:
    print("No value") # Output: No value
```

## 2. Systems Path (Internals / C-Interop)
The `None` singleton ID.

```python
import sys
# None is a unique object in memory
print(hex(id(None)))
```

## 3. Portable Path (Zero-Dependency)
Using `None` as a default return or argument sentinel.

```python
def check(val=None):
    return val or "Default"
```

## 4. Strict Path (Type-Hinted)
Using `Optional` (Union with None).

```python
from typing import Optional
user_name: Optional[str] = None
```

# The Logic Bridge
// Logic: `None` is a singleton instance of the `NoneType` class. In Python's C source, it is represented as `_Py_NoneStruct`. Using `is None` is more efficient than `== None` because it performs a pointer comparison rather than a value check.
