# Inheritance (PRO)

Definition: Allowing a class to derive attributes and methods from a parent class.

## 1. Modern Path (3.12+ / Idiomatic)
Using `super()` for cooperative inheritance.

```python
class Parent:
    def start(self): print("Parent Start")

class Child(Parent):
    def start(self):
        super().start()
        print("Child Start")
```

## 2. Systems Path (Internals / C-Interop)
The `__bases__` and `__mro__` attributes.

```python
class X: pass
class Y(X): pass
print(Y.__bases__) # Output: (<class '__main__.X'>,)
```

## 3. Portable Path (Zero-Dependency)
Basic inheritance check.

```python
print(issubclass(Child, Parent)) # Output: True
```

## 4. Strict Path (Type-Hinted)
Typed method overrides.

```python
class Parent:
    def log(self, msg: str) -> None: pass

class Child(Parent):
    def log(self, msg: str) -> None:
        print(msg)
```

# The Logic Bridge
// Logic: Inheritance in Python is dynamic. When a method is called, Python searches the instance's dictionary, then the class's, and then follows the **C3 Linearization** (MRO) path to resolve the symbol.
