# Abstract Classes & ABC (PRO)

Definition: Defining a contract (interface) that subclasses must implement using the `abc` module.

## 1. Modern Path (3.12+ / Idiomatic)
Using the `@abstractmethod` decorator.

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self) -> float: pass
```

## 2. Systems Path (Internals / C-Interop)
The `__abstractmethods__` attribute.

```python
# s = Shape() # TypeError: Can't instantiate abstract class...
print(Shape.__abstractmethods__) # frozenset({'area'})
```

## 3. Portable Path (Zero-Dependency)
Manual `NotImplementedError` (Legacy Interface style).

```python
class Base:
    def run(self): raise NotImplementedError()
```

## 4. Strict Path (Type-Hinted)
Full interface implementation verification.

```python
class Square(Shape):
    def area(self) -> float: return 1.0
```

# The Logic Bridge
// Logic: Abstract Base Classes (ABC) prevent instantiation by adding a check in the `__new__` method of the class. If any abstract methods are not overridden in the subclass, the VM raises a `TypeError` during construction.
