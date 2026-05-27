# 29 - Passing Mechanisms (CORE)

Definition: Python uses "Pass-by-Object-Reference" (also called Pass-by-Assignment). You aren't passing the variable itself, but a pointer to the object. Whether the object is **Mutable** or **Immutable** determines if changes persist outside the function.

## 1. Modern Path (3.12+ / Idiomatic)
Passing immutable (int, str) vs mutable (list, dict).

```python
def modify(n, l):
    n = n + 1   # Local assignment (New object)
    l.append(4) # In-place modification

x = 1
y = [1, 2, 3]
modify(x, y)
print(f"x: {x}, y: {y}") # Output: x: 1, y: [1, 2, 3, 4]
```

## 2. Systems Path (Internals / C-Interop)
Examining reference IDs before and after function calls.

```python
def check_id(obj):
    print(f"Inside: {id(obj)}")

val = [1]
print(f"Outside: {id(val)}")
check_id(val) # IDs will match
```

## 3. Portable Path (Zero-Dependency)
Avoiding the "Mutable Default Argument" trap.

```python
# BAD: def append_to(val, list=[]):
def append_to(val, list=None):
    if list is None: list = []
    list.append(val)
    return list
```

## 4. Strict Path (Type-Hinted)
Using `Final` for parameter-like constants.

```python
from typing import List

def process_data(data: List[int]) -> int:
    return sum(data)
```

# The Logic Bridge
// Logic: In Python, assignments don't copy data; they copy pointers. When you pass a list to a function, both the outer variable and the inner parameter point to the same memory address. Since lists are mutable, calling `.append()` affects the original object. Since integers are immutable, `n + 1` creates a brand new integer object and points the local name `n` to it, leaving the original unchanged.
