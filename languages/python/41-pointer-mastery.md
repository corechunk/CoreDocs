# 48 - Pointer Mastery (SYSTEMS)

Definition: Interacting with raw memory addresses.

## 1. Modern Path (3.12+ / Idiomatic)
Passing Python objects to C-libraries.

```python
import ctypes
libc = ctypes.CDLL("libc.so.6")
libc.printf(b"Hello from C\n")
```

## 2. Systems Path (Internals / C-Interop)
Raw pointer manipulation.

```python
import ctypes
x = ctypes.c_int(42)
ptr = ctypes.pointer(x)
print(ptr.contents) # Output: c_int(42)
```

## 3. Portable Path (Zero-Dependency)
Using `id()` to see the pointer value.

```python
x = 1
print(f"Object Pointer: {id(x)}")
```

## 4. Strict Path (Type-Hinted)
Typed C-pointers.

```python
from ctypes import POINTER, c_int
p_int: POINTER(c_int)
```

# The Logic Bridge
// Logic: Python objects are always accessed via pointers in the C source. When you use `ctypes`, you are breaking the safety of the VM and interacting directly with the process's address space, requiring manual management of memory to avoid segmentation faults.
