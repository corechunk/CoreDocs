# Integers (CORE)

Definition: Python integers are arbitrary-precision objects. They handle arbitrarily large numbers automatically and provide bitwise manipulation capabilities.

## 1. Modern Path (3.12+ / Idiomatic)
Using large integers and underscored literals for readability.

```python
val = 1_000_000_000
power = 2 ** 100 # No overflow
print(f"Result: {power}")
```

## 2. Systems Path (Internals / C-Interop)
Examining the `PyObject` structure and memory size.

```python
import sys
x = 0
print(f"Zero size: {sys.getsizeof(x)} bytes")
# Logic: Even 0 takes memory for reference counting and type pointers.
```

## 3. Portable Path (Zero-Dependency)
Base conversions (Hex, Bin, Oct).

```python
x = 255
print(bin(x)) # 0b11111111
print(hex(x)) # 0xff
```

## 4. Strict Path (Type-Hinted)
Explicit integer typing.

```python
count: int = 42
```

# The Logic Bridge
// Logic: Python integers are implemented as a C struct (`PyLongObject`) containing an array of "digits" (usually 30-bit chunks). This allows them to scale memory usage dynamically to represent any number that fits in your RAM.
