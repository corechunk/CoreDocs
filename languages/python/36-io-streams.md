# 36 - IO Streams (CORE)

Definition: Managing input and output streams (`stdin`, `stdout`, `stderr`) and file access.

## 1. Modern Path (3.12+ / Idiomatic)
Using `pathlib` for modern file handling.

```python
from pathlib import Path
p = Path("test.txt")
p.write_text("Modern IO")
print(p.read_text()) # Output: Modern IO
```

## 2. Systems Path (Internals / C-Interop)
Direct interaction with `sys.stdout` and file descriptors.

```python
import sys
import os
sys.stdout.write("Direct stdout\n")
fd = os.open("raw.bin", os.O_RDWR | os.O_CREAT)
os.write(fd, b"\x01\x02")
os.close(fd)
```

## 3. Portable Path (Zero-Dependency)
The standard `open` built-in.

```python
with open("file.txt", "w") as f:
    f.write("Standard")
```

## 4. Strict Path (Type-Hinted)
Using `TextIO` and `BinaryIO`.

```python
from typing import TextIO
def process_stream(stream: TextIO):
    stream.write("Typed Data")
```

# The Logic Bridge
// Logic: Python's `open()` returns a "File Object" which is a buffered wrapper around a raw OS file descriptor. The `with` statement (Context Manager) ensures the `close()` system call is triggered even if an exception occurs, preventing file descriptor leaks.
