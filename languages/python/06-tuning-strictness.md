# 06 - Tuning & Strictness (PRO)

Definition: Enforcing code quality and performance via tools and flags.

## 1. Modern Path (3.12+ / Idiomatic)
Using `ruff` or `flake8` for linting.

```bash
# ruff check .
```

## 2. Systems Path (Internals / C-Interop)
Disabling GC for critical loops.

```python
import gc
gc.disable()
# ... tight loop ...
gc.enable()
```

## 3. Portable Path (Zero-Dependency)
Basic assertions.

```python
assert 1 > 0, "Logic fail"
```

## 4. Strict Path (Type-Hinted)
Full static checking.

```bash
# mypy --strict script.py
```

# The Logic Bridge
// Logic: Python's dynamic nature can be "hardened" using static analyzers. At runtime, flags like `-O` remove assertions, while `gc.disable()` prevents the cyclic garbage collector from triggering during latency-sensitive operations.
