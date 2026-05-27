# 37 - Procedural Mechanisms (PRO)

Definition: Top-level execution and module-based logic.

## 1. Modern Path (3.12+ / Idiomatic)
Modular organization.

```python
# In core.py
def start(): print("Proc start")
```

## 2. Systems Path (Internals / C-Interop)
The `sys.modules` cache and import hooks.

```python
import sys
print(sys.modules['os']) # Shows cached module object
```

## 3. Portable Path (Zero-Dependency)
Standard imports.

```python
import math
print(math.sqrt(16))
```

## 4. Strict Path (Type-Hinted)
Explicitly typed module interfaces.

```python
__all__ = ["start"] # Export control
```

# The Logic Bridge
// Logic: Python code is executed line-by-line during the import phase. The `sys.modules` dictionary acts as a singleton cache to ensure each module is only executed once per process.
