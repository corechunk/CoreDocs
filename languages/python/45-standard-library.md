# Standard Library (PRO)

Definition: The "Batteries Included" set of modules provided with Python.

## 1. Modern Path (3.12+ / Idiomatic)
Key modern modules: `pathlib`, `zoneinfo`, `graphlib`.

```python
import zoneinfo
now = zoneinfo.ZoneInfo("UTC")
```

## 2. Systems Path (Internals / C-Interop)
Low-level modules: `ctypes`, `dis`, `inspect`, `sys`.

```python
import inspect
print(inspect.getsource(zoneinfo))
```

## 3. Portable Path (Zero-Dependency)
Core modules: `os`, `sys`, `re`, `json`.

```python
import json
data = json.dumps({"ok": True})
```

## 4. Strict Path (Type-Hinted)
Standard types from `typing` and `collections.abc`.

```python
from collections.abc import Iterable
def proc(data: Iterable[int]): pass
```

# The Logic Bridge
// Logic: The Python Standard Library is a mix of pure Python code and highly optimized C modules. This provides a consistent cross-platform API for everything from file access to cryptography.
