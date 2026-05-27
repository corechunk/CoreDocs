# 16 - Syntactic Automation (SYSTEMS)

Definition: Features where Python generates code or behavior automatically, such as Decorators, Context Managers, and Metaclasses.

## 1. Modern Path (3.12+ / Idiomatic)
Using `dataclasses` for automatic boilerplate.

```python
from dataclasses import dataclass

@dataclass
class Point:
    x: int
    y: int

p = Point(1, 2)
print(p) # Output: Point(x=1, y=2)
```

## 2. Systems Path (Internals / C-Interop)
Custom Metaclasses to control class creation.

```python
class Meta(type):
    def __new__(cls, name, bases, dct):
        print(f"Creating {name}")
        return super().__new__(cls, name, bases, dct)

class Auto(metaclass=Meta): pass
# Output: Creating Auto
```

## 3. Portable Path (Zero-Dependency)
Basic Decorators.

```python
def log(f):
    def wrapper(*args):
        print("Calling...")
        return f(*args)
    return wrapper

@log
def hello(): print("Hi")
```

## 4. Strict Path (Type-Hinted)
Protocol-based automation (Structural Typing).

```python
from typing import Protocol

class Drawable(Protocol):
    def draw(self) -> None: ...

def render(obj: Drawable):
    obj.draw()
```

# The Logic Bridge
// Logic: Syntactic automation in Python is powered by "Hooks." For example, `@dataclass` inspects the class's type hints and injects generated `__init__`, `__repr__`, and `__eq__` methods directly into the class's `__dict__` during the import phase.
