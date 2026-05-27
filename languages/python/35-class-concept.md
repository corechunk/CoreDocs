# 35 - Class Concept (CORE - Hub)

Definition: The `class` is the gateway to Object-Oriented Programming. It allows for the creation of objects that encapsulate **State** (Attributes) and **Behavior** (Methods).

## Deep-Dive Reference
For complex hierarchies and pillars:
- [Advanced OOP](./oop/00-start.md)

---

## 1. Modern Path (3.12+ / Idiomatic)
Standard class with primary-like init and methods.

```python
class Counter:
    def __init__(self, start: int = 0):
        self.value = start
    
    def inc(self):
        self.value += 1

c = Counter(10)
c.inc()
print(c.value) # Output: 11
```

## 2. Systems Path (Internals / C-Interop)
Examining method binding and the `__dict__`.

```python
class Entity: pass
e = Entity()
e.id = 1
print(e.__dict__) # Output: {'id': 1}
# Logic: Shows how instance state is stored in a hash map.
```

## 3. Portable Path (Zero-Dependency)
Inheritance-based state sharing.

```python
class Base:
    def __init__(self): self.active = True

class App(Base):
    def run(self): print(self.active)

App().run() # Output: True
```

## 4. Strict Path (Type-Hinted)
Explicit `self` typing and return hints.

```python
from typing import Self

class Node:
    def __init__(self, val: int):
        self.val: int = val
    
    def get_self(self) -> Self:
        return self
```

# The Logic Bridge
// Logic: In Python, methods are actually class attributes that are "Bound" to an instance at runtime. The `self` argument is the explicit mechanism the VM uses to pass the object's instance pointer into the method's local frame.
