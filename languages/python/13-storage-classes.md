# 13 - Storage Classes (SYSTEMS)

Definition: Management of variable persistence and visibility across scopes. Python uses `global` and `nonlocal` keywords to modify name binding behavior.

## 1. Modern Path (3.12+ / Idiomatic)
Using local function variables (Most common storage).

```python
def process():
    data = [1, 2, 3] # Stack-allocated reference
    return sum(data)
```

## 2. Systems Path (Internals / C-Interop)
Interning and object reuse in the CPython VM.

```python
import sys
a = "hello"
b = "hello"
print(a is b) # Output: True (Interned string)

x = 256
y = 256
print(x is y) # Output: True (Small integer cache)
```

## 3. Portable Path (Zero-Dependency)
Using `global` for cross-scope access.

```python
state = "init"
def update():
    global state
    state = "ready"
```

## 4. Strict Path (Type-Hinted)
Enforcing local binding and avoiding global state.

```python
from typing import Final
CONFIG: Final = {"port": 80}
```

# The Logic Bridge
// Logic: Python uses "Namespaces" (dictionaries) to manage storage. CPython optimizes storage for small integers (-5 to 256) and certain strings by "Interning" them—reusing the same memory address for identical values to save space and speed up comparisons.
