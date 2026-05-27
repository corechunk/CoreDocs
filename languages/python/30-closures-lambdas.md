# 30 - Closures & Lambdas (PRO)

Definition: Anonymous functions (`lambda`) and nested functions that capture their environment (Closures).

## 1. Modern Path (3.12+ / Idiomatic)
Lambdas for quick logic.

```python
sq = lambda x: x * x
print(sq(5)) # Output: 25
```

## 2. Systems Path (Internals / C-Interop)
Inspecting the `__closure__` attribute and cell objects.

```python
def make_adder(x):
    def adder(y): return x + y
    return adder

add5 = make_adder(5)
print(add5.__closure__[0].cell_contents) # Output: 5
```

## 3. Portable Path (Zero-Dependency)
Standard function nesting.

```python
def outer(msg):
    def inner(): print(msg)
    return inner
```

## 4. Strict Path (Type-Hinted)
Typed closures using `Callable`.

```python
from typing import Callable
def get_func() -> Callable[[int], int]:
    return lambda x: x + 1
```

# The Logic Bridge
// Logic: Closures work by creating "Cell" objects. When an inner function references a variable from an outer scope, the VM stores that variable in a cell that persists even after the outer function has finished executing, effectively "closing over" the state.
