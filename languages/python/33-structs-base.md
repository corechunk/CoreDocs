# 33 - Structs Base (CORE - Hub)

Definition: Python uses `dataclass` and `NamedTuple` as the gateway to Procedural-style data modeling. They provide a lightweight way to group variables without the boilerplate of a full class.

## Deep-Dive Reference
For modular procedural architecture:
- [Procedural Mechanisms](./procedural/00-start.md)

---

## 1. Modern Path (3.12+ / Idiomatic)
Using `@dataclass` for clear data grouping.

```python
from dataclasses import dataclass

@dataclass
class Config:
    host: str
    port: int

c = Config("localhost", 80)
print(f"{c.host}:{c.port}") # Output: localhost:80
```

## 2. Systems Path (Internals / C-Interop)
Using `collections.namedtuple` for memory-efficient C-like records.

```python
from collections import namedtuple
import sys

Config = namedtuple("Config", ["host", "port"])
c = Config("127.0.0.1", 443)
print(f"Size: {sys.getsizeof(c)} bytes") # Logic: Fixed-size buffer
```

## 3. Portable Path (Zero-Dependency)
Standard class used as a simple data container.

```python
class Data:
    def __init__(self, x, y):
        self.x = x
        self.y = y

d = Data(10, 20)
```

## 4. Strict Path (Type-Hinted)
Using `typing.NamedTuple` for rigid, typed records.

```python
from typing import NamedTuple

class Connection(NamedTuple):
    address: str
    port: int

conn: Connection = Connection("192.168.1.1", 8080)
```

# The Logic Bridge
// Logic: While a standard class in Python is a heavyweight object with a `__dict__`, a `namedtuple` is a memory-efficient C-structure in the VM, acting as the perfect procedural bridge between raw data and objects.
