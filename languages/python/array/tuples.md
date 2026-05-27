# Tuples (CORE)

Definition: `tuple` is an immutable sequence. Once created, its size and contents cannot be changed.

## 1. Modern Path (3.12+ / Idiomatic)
Structural unpacking and singleton tuples.

```python
point = (10, 20)
x, y = point

single = (1,) # Comma required for singleton
```

## 2. Systems Path (Internals / C-Interop)
Immutability and memory efficiency.

```python
import sys
t = (1, 2, 3)
# t[0] = 5 # TypeError: 'tuple' object does not support item assignment
print(f"Tuple size: {sys.getsizeof(t)}")
```

## 3. Portable Path (Zero-Dependency)
Tuples as dictionary keys (Hashable).

```python
locations = { (40.7, -74.0): "New York" }
print(locations[(40.7, -74.0)]) # Output: New York
```

## 4. Strict Path (Type-Hinted)
Fixed-length tuple typing.

```python
from typing import Tuple
coords: Tuple[int, int] = (100, 200)
```

# The Logic Bridge
// Logic: Tuples are faster than lists because their immutability allows Python to store them in a fixed-size C structure without the overhead of dynamic growth logic. They are "Hashable" because their contents are guaranteed not to change.
