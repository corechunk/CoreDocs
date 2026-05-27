# Modules (PRO)

Definition: A module is a single Python file containing code that can be imported and reused.

## 1. Modern Path (3.12+ / Idiomatic)
Modern import syntax and `__name__` guard.

```python
import sys
from os import path

if __name__ == "__main__":
    print(f"Running as script: {path.basename(__file__)}")
```

## 2. Systems Path (Internals / C-Interop)
Inspecting the module object and its dictionary.

```python
import os
print(type(os)) # <class 'module'>
print(os.__dict__.keys()) # Symbols in the module
```

## 3. Portable Path (Zero-Dependency)
Relative imports within a project.

```python
# from . import utils
```

## 4. Strict Path (Type-Hinted)
Typed module handles.

```python
import types
def process_mod(m: types.ModuleType):
    print(m.__name__)
```

# The Logic Bridge
// Logic: Importing a module triggers the interpreter to search `sys.path`, compile the file to bytecode, and execute it in its own private namespace. The resulting module object is then cached in `sys.modules`.
