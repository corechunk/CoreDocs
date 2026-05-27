# 53 - Build Tools (PRO)

Definition: Managing dependencies and distribution.

## 1. Modern Path (3.12+ / Idiomatic)
`poetry`, `uv`, or `pip-compile`.

```bash
# uv pip install ruff
```

## 2. Systems Path (Internals / C-Interop)
Wheels and C-extension building.

```bash
# python setup.py bdist_wheel
```

## 3. Portable Path (Zero-Dependency)
`pip` and `requirements.txt`.

```bash
python -m pip install -r requirements.txt
```

## 4. Strict Path (Type-Hinted)
Dependency constraints.

```text
requests==2.31.0
```

# The Logic Bridge
// Logic: Build tools resolve the dependency graph and install packages into the environment. Wheels (`.whl`) are binary distributions that allow Python to ship pre-compiled C-extensions, avoiding the need for the user to have a C-compiler installed.
