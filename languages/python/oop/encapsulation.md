# Encapsulation (PRO)

Definition: Bundling data and methods into a single unit and restricting access. In Python, this is achieved by convention (`_` and `__`) and properties.

## 1. Modern Path (3.12+ / Idiomatic)
Using decorators for properties.

```python
class User:
    def __init__(self, name):
        self._name = name
    
    @property
    def name(self):
        return self._name
```

## 2. Systems Path (Internals / C-Interop)
Name mangling internals for `__private` attributes.

```python
class Test:
    def __init__(self): self.__secret = 42

t = Test()
# Accessing mangled attribute
print(t._Test__secret) # Output: 42
```

## 3. Portable Path (Zero-Dependency)
Standard underscore convention.

```python
class Config:
    def __init__(self):
        self._port = 80
```

## 4. Strict Path (Type-Hinted)
Using `typing` for protected members.

```python
class Account:
    def __init__(self, bal: float):
        self.__balance: float = bal
```

# The Logic Bridge
// Logic: Python does not have true private members. Name mangling (`__var`) is a safety feature that changes the attribute name in the instance's `__dict__` to include the class name, making accidental overrides difficult but not impossible.
