# 23 - Iteration: Definite (CORE)

Definition: Definite iteration executes a block of code a specific number of times or for each element in a collection. Python uses `for` loops with the `iterator` protocol.

## 1. Modern Path (3.12+ / Idiomatic)
Iterating with `enumerate` and `zip`.

```python
names = ["Core", "Chunk"]
for i, name in enumerate(names):
    print(f"{i}: {name}") # Output: 0: Core, 1: Chunk
```

## 2. Systems Path (Internals / C-Interop)
The Iterator Protocol: `__iter__` and `__next__`.

```python
nums = [1, 2]
it = iter(nums)
print(next(it)) # Output: 1
print(next(it)) # Output: 2
# next(it) triggers StopIteration exception
```

## 3. Portable Path (Zero-Dependency)
Standard `range` based loops.

```python
for i in range(3):
    print(i, end=" ") # Output: 0 1 2 
```

## 4. Strict Path (Type-Hinted)
Iterating over strictly typed collections.

```python
from typing import List

data: List[int] = [10, 20, 30]
for item in data:
    val: int = item
    print(val) # Output: 10 20 30
```

# The Logic Bridge
// Logic: Python's `for` loop is actually a `while` loop that calls `next()` on an iterator and catches the `StopIteration` exception to exit. The `range()` function does not create a list in memory; it is a "Generator-like" object that computes the next value on-the-fly, making it memory efficient for large ranges.
