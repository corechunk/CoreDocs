# Mixins & MRO (PRO)

Definition: Mixins are small, specialized classes used to add functionality via multiple inheritance. MRO (Method Resolution Order) is the path Python takes to find symbols.

## 1. Modern Path (3.12+ / Idiomatic)
Simple JSON Mixin.

```python
import json

class JsonMixin:
    def to_json(self): return json.dumps(self.__dict__)

class Data(JsonMixin):
    def __init__(self, x): self.x = x

d = Data(10)
print(d.to_json()) # Output: {"x": 10}
```

## 2. Systems Path (Internals / C-Interop)
Calculating the MRO order.

```python
class A: pass
class B(A): pass
class C(A): pass
class D(B, C): pass

print(D.mro()) # Path: D -> B -> C -> A -> object
```

## 3. Portable Path (Zero-Dependency)
Standard Multiple Inheritance.

```python
class PluginA: pass
class PluginB: pass
class App(PluginA, PluginB): pass
```

## 4. Strict Path (Type-Hinted)
Enforcing MRO order in complex hierarchies.

```python
from typing import Type
def check_mro(cls: Type):
    print(cls.mro())
```

# The Logic Bridge
// Logic: Python uses the **C3 Linearization** algorithm. It ensures three properties: sub-class priority, left-to-right priority (order in parent list), and monotonicity (order is stable regardless of where you start).
