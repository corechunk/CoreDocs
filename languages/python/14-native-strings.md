# 14 - Native Strings (PRO)

Definition: High-performance string manipulation using built-in methods and slicing.

## 1. Modern Path (3.12+ / Idiomatic)
Case folding and modern methods like `removeprefix`.

```python
s = "Python_v2"
print(s.removeprefix("Python_")) # Output: v2
print("ẞ".casefold()) # Output: ss
```

## 2. Systems Path (Internals / C-Interop)
Direct memory access to string buffers via `ctypes`.

```python
import ctypes
s = "Hello"
addr = id(s) + 48 # Offset to buffer in CPython 3.12
print(ctypes.string_at(addr, 5))
```

## 3. Portable Path (Zero-Dependency)
Slicing and splitting.

```python
text = "alpha,beta,gamma"
parts = text.split(",")
print(text[:5]) # Output: alpha
```

## 4. Strict Path (Type-Hinted)
Ensuring string inputs and outputs.

```python
def parser(data: str) -> list[str]:
    return data.strip().split()
```

# The Logic Bridge
// Logic: Python strings are immutable. Operations like `strip()` or `split()` create new string objects in memory. The C-layer handles the copy-on-write-like behavior to ensure that modifications to one string name do not corrupt others pointing to the same buffer.
