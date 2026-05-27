# 02 - Compilation & Run Basics (CORE)

Definition: Python is an interpreted language, but it compiles source code (`.py`) into Bytecode (`.pyc`) before execution. The Virtual Machine (VM) then executes the bytecode instructions.

## 1. Modern Path (3.12+ / Idiomatic)
Running scripts directly and using the `__main__` guard.

```python
def main():
    print("Hello Modern Python")

if __name__ == "__main__":
    main()
# Output: Hello Modern Python
```

## 2. Systems Path (Internals / C-Interop)
Generating and inspecting bytecode files.

```bash
# COMPILE TO BYTECODE
python3 -m py_compile main.py

# INSPECT .pyc
# Found in __pycache__/main.cpython-312.pyc
```

## 3. Portable Path (Zero-Dependency)
The Shebang ritual for Unix systems.

```python
#!/usr/bin/env python3
print("Portable Execution")
```

## 4. Strict Path (Type-Hinted)
Running with optimization and strict flags.

```bash
python3 -O main.py # Optimized (removes asserts)
python3 -X dev main.py # Enable Development Mode (runtime checks)
```

# The Logic Bridge
// Logic: The `.pyc` file contains the `PyCodeObject` serialized into a platform-independent format. This allows Python to skip the parsing and compilation phase on subsequent runs. The VM executes this bytecode using a stack-based architecture.
