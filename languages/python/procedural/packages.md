# Packages (PRO)

Definition: A package is a directory containing a special `__init__.py` file (or none in implicit namespace packages) that groups multiple modules.

## 1. Modern Path (3.12+ / Idiomatic)
Namespace packages (no `__init__.py` required in 3.3+).

```python
# structure:
# my_pkg/
#   core.py
#   utils.py
```

## 2. Systems Path (Internals / C-Interop)
The `__path__` attribute and package locations.

```python
import json
print(json.__path__) # Shows absolute path on disk
```

## 3. Portable Path (Zero-Dependency)
Exposing symbols via `__init__.py`.

```python
# In __init__.py:
# from .core import run
# __all__ = ["run"]
```

## 4. Strict Path (Type-Hinted)
Enforcing package boundaries.

```python
__package__: str = "my_pkg"
```

# The Logic Bridge
// Logic: Packages allow for hierarchical namespaces. When a package is imported, its `__init__.py` is executed, allowing for package-level initialization and controlled exposure of internal module symbols.
