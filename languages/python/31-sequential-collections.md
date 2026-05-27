# 31 - Sequential Collections (CORE - Hub)

Definition: Sequential collections store items in a specific order. In Python, the primary types are `list` (mutable) and `tuple` (immutable).

## 1. Modern Path (3.12+ / Idiomatic)
List comprehensions and slicing.

```python
nums = [x for x in range(5)]
print(nums[::-1]) # Reverse slice. Output: [4, 3, 2, 1, 0]
```

## 2. Systems Path (Internals / C-Interop)
The size difference between `list` and `tuple`.

```python
import sys
l = [1, 2, 3]
t = (1, 2, 3)
print(f"List: {sys.getsizeof(l)}, Tuple: {sys.getsizeof(t)}")
# Logic: Tuples are smaller as they are fixed-size in C.
```

## 3. Portable Path (Zero-Dependency)
Basic list operations.

```python
items = []
items.append("A")
items.extend(["B", "C"])
print(items) # Output: ['A', 'B', 'C']
```

## 4. Strict Path (Type-Hinted)
Typed lists and tuples.

```python
from typing import List, Tuple

data: List[int] = [1, 2, 3]
point: Tuple[int, int] = (10, 20)
```

# The Logic Bridge
// Logic: A Python `list` is not a linked list; it is a dynamic array of pointers (`PyObject**`). When it fills up, Python over-allocates memory to make future `append` operations O(1). A `tuple` is a fixed-length array of pointers, making it faster and memory-efficient for static data.
