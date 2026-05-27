# 38 - Advanced OOP (PRO - Hub)

Definition: Multiple inheritance, Mixins, and Abstract Base Classes (ABC).

## Deep-Dive Reference
For complex hierarchies and abstractions:
- [Encapsulation](./encapsulation.md) | [Inheritance](./inheritance.md)
- [Polymorphism](./polymorphism.md) | [Abstract Classes](abstract-classes.md)
- [Mixins & MRO](./mixins.md)

---

## 1. Modern Path (3.12+ / Idiomatic)
Using `super()` and property decorators.

```python
class Base:
    def log(self): print("Base")

class Derived(Base):
    def log(self):
        super().log()
        print("Derived")
```

## 2. Systems Path (Internals / C-Interop)
Inspecting the Method Resolution Order (MRO).

```python
class A: pass
class B(A): pass
print(B.mro()) # Output: [B, A, object]
```

## 3. Portable Path (Zero-Dependency)
Basic class structures.

```python
class Simple: pass
```

## 4. Strict Path (Type-Hinted)
Using `abc.ABC` for strict interfaces.

```python
from abc import ABC, abstractmethod

class Service(ABC):
    @abstractmethod
    def execute(self) -> None: pass
```

# The Logic Bridge
// Logic: Python uses the **C3 Linearization** algorithm to determine MRO. This ensures that in complex diamond inheritance, each parent is visited once in a predictable, stable order.
