# 47 - Memory Allocation (SYSTEMS)

Definition: Low-level memory acquisition.

## 1. Modern Path (3.12+ / Idiomatic)
Memoryviews for zero-copy slicing.

```python
data = bytearray(b"Corechunk")
v = memoryview(data)
sub = v[0:4] # No copy created
```

## 2. Systems Path (Internals / C-Interop)
Manual allocation via `ctypes`.

```python
import ctypes
# Allocate 1024 bytes of raw memory
buf = ctypes.create_string_buffer(1024)
```

## 3. Portable Path (Zero-Dependency)
`bytearray` for mutable buffers.

```python
b = bytearray(10)
b[0] = 255
```

## 4. Strict Path (Type-Hinted)
Explicitly typed buffers.

```python
from typing import ByteString
def raw_proc(data: ByteString): pass
```

# The Logic Bridge
// Logic: CPython uses a specialized memory allocator called `pymalloc`, which is optimized for small object allocations (< 512 bytes). Large allocations are passed directly to the OS's `malloc` or `mmap`.
