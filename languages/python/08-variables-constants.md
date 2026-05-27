# 08 - Variables & Constants (CORE)

Definition: Python variables are names pointing to objects in memory. They are dynamically typed (re-assignable to different types), but type-checking can be enforced. Constants are a convention, as Python has no native `const` keyword.

## 1. Modern Path (3.12+ / Idiomatic)
Using basic variable assignment and the `type` function.

```python
user = "Corechunk"
count = 5

# Re-assignment (Dynamic)
count = "five"

print(f"{user}: {count}") # Output: Corechunk: five
```

## 2. Systems Path (Internals / C-Interop)
Looking at variable addresses and object IDs in the CPython VM.

```python
import sys

x = 1000
# id() returns the memory address of the object
print(f"Address: {hex(id(x))}") 
print(f"Size in bytes: {sys.getsizeof(x)}") # Output: 28 (Int object overhead)
```

## 3. Portable Path (Zero-Dependency)
Standard variable naming and global access.

```python
VERSION = "1.0.0" # Conventional constant

def show_version():
    print(VERSION)

show_version() # Output: 1.0.0
```

## 4. Strict Path (Type-Hinted)
Enforcing immutability with `Final` and explicit type annotations.

```python
from typing import Final

# Annotated variable
user_id: int = 101

# Final constant (Requires static analyzer check)
LIMIT: Final[int] = 10

# user_id = "text" # Static error (mypy)
print(user_id) # Output: 101
```

# The Logic Bridge
// Logic: Python variables are actually pointers to `PyObject` structs on the heap. When you assign `x = 5`, `x` is a name in the local namespace (a dict) that stores the address of the integer object `5`. `Final` doesn't prevent runtime modification; it is a contract for static analysis tools to ensure architectural integrity.
