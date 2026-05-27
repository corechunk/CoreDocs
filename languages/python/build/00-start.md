# 52 - Multi-File Projects (PRO)

Definition: Organizing code via Modules and Packages.

## 1. Modern Path (3.12+ / Idiomatic)
Package structure with `__init__.py` and relative imports.

```python
from .utils import start
```

## 2. Systems Path (Internals / C-Interop)
Inspecting `sys.path` and site-packages.

```python
import sys
print(sys.path)
```

## 3. Portable Path (Zero-Dependency)
Flat directory modules.

```python
import my_module
```

## 4. Strict Path (Type-Hinted)
Explicit namespace control.

```python
from typing import TYPE_CHECKING
if TYPE_CHECKING:
    import heavy_module
```

# The Logic Bridge
// Logic: An "Import" in Python triggers a search through `sys.path`. Once found, the code is executed and the result is stored in `sys.modules`. Future imports of the same name simply return the cached object.
