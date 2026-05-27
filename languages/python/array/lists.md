# Lists (CORE)

Definition: `list` is a mutable, dynamic array of object references.

## 1. Modern Path (3.12+ / Idiomatic)
List unpacking and comprehensions.

```python
head, *tail = [1, 2, 3, 4]
squares = [x*x for x in range(10) if x % 2 == 0]
print(f"Tail: {tail}") # Output: Tail: [2, 3, 4]
```

## 2. Systems Path (Internals / C-Interop)
Examining how lists grow in memory.

```python
import sys
l = []
print(f"Empty size: {sys.getsizeof(l)}") 
l.append(1)
print(f"After append: {sys.getsizeof(l)}") 
# Logic: Lists over-allocate to ensure O(1) appends.
```

## 3. Portable Path (Zero-Dependency)
Standard append/extend/sort operations.

```python
items = ["z", "a"]
items.sort()
items.append("b")
print(items) # Output: ['a', 'b', 'z']
```

## 4. Strict Path (Type-Hinted)
Generic list typing.

```python
from typing import List
data: List[str] = ["Core", "Chunk"]
```

# The Logic Bridge
// Logic: A Python list is not a linked list; it is a contiguous array of pointers to objects. When the array is full, Python allocates a new, larger array and moves the pointers, providing O(1) average time complexity for appends.
