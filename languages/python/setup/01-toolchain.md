# 01 - Toolchain Installation (CORE)

Definition: The Python toolchain includes the interpreter (`python3`), package managers (`pip`), and environment managers (`venv`). Standardizing installation via `mise` ensures consistency across systems.

## 1. Modern Path (3.12+ / Idiomatic)
Using `mise` to manage Python versions.

```bash
# INSTALL
mise use python@3.12

# VERSION CHECK
python --version
# Output: Python 3.12.0
```

## 2. Systems Path (Internals / C-Interop)
Locating the shared library and include headers for C-interop.

```bash
# LOCATE LIB
python3-config --ldflags
# Output: -L/usr/lib -lpython3.12

# LOCATE HEADERS
python3-config --includes
# Output: -I/usr/include/python3.12
```

## 3. Portable Path (Zero-Dependency)
Checking for the pre-installed system Python.

```bash
/usr/bin/python3 --version
# Output: Python 3.x.x
```

## 4. Strict Path (Type-Hinted)
Enforcing environment isolation via `venv`.

```bash
python3 -m venv .venv
source .venv/bin/activate
python3 -m pip install mypy # For strict type checking
```

# The Logic Bridge
// Logic: The Python interpreter is a C binary that links against `libpython`. At the system level, Python relies on a search path (`sys.path`) to locate modules. Using `venv` ensures that the interpreter uses a local `site-packages` directory, preventing global dependency conflicts.
