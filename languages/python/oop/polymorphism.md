# Polymorphism (PRO)

Definition: The ability of different types to be treated as a common type. In Python, this is primarily achieved via Duck Typing and method overriding.

## 1. Modern Path (3.12+ / Idiomatic)
Duck typing in action.

```python
class Cat:
    def speak(self): print("Meow")

class Dog:
    def speak(self): print("Woof")

def animal_sound(animal):
    animal.speak()
```

## 2. Systems Path (Internals / C-Interop)
The `PyObject` type pointer and dynamic dispatch.

```python
# id(animal.speak) shows the method object address
```

## 3. Portable Path (Zero-Dependency)
Overriding base class methods.

```python
class Base:
    def action(self): pass

class Sub(Base):
    def action(self): print("Sub")
```

## 4. Strict Path (Type-Hinted)
Using `Protocols` for structural subtyping.

```python
from typing import Protocol

class Speaker(Protocol):
    def speak(self) -> None: ...

def make_speak(s: Speaker):
    s.speak()
```

# The Logic Bridge
// Logic: Polymorphism in Python is "late-bound." The interpreter looks up the method name in the object's attribute dictionary at the moment of the call. If the name exists and is callable, it executes, regardless of the object's inheritance chain.
