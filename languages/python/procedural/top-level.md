# Top-Level Execution (PRO)

Definition: Code that executes in the global scope of a module. In Python, this is where initialization logic and the `__main__` entry point reside.

## 1. Modern Path (3.12+ / Idiomatic)
The `if __name__ == "__main__"` pattern.

```python
def start(): print("System Boot")

if __name__ == "__main__":
    start() # Only runs if executed directly
```

## 2. Systems Path (Internals / C-Interop)
The `__dict__` of the `__main__` module.

```python
import sys
# print(sys.modules['__main__'].__dict__)
```

## 3. Portable Path (Zero-Dependency)
Global variable initialization.

```python
import os
HOME = os.getenv("HOME")
```

## 4. Strict Path (Type-Hinted)
Enforcing types for global configuration.

```python
from typing import Final
DEBUG: Final[bool] = True
```

# The Logic Bridge
// Logic: Python code is interpreted top-to-bottom. When a file is imported, all top-level statements execute immediately. The `__name__` check allows a file to serve dual roles as both a reusable module and a standalone executable script.
