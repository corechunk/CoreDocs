# 32 - Associative Collections (CORE - Hub)

Definition: Associative collections store data as key-value pairs. In Python, these are `dict` (Hash Map) and `set` (Unique collection).

## 1. Modern Path (3.12+ / Idiomatic)
Dictionary comprehensions and merging.

```python
base = {"a": 1}
update = {"b": 2}
merged = base | update # Modern merge operator (3.9+)
print(merged) # Output: {'a': 1, 'b': 2}
```

## 2. Systems Path (Internals / C-Interop)
Hash collisions and bucket internals.

```python
# hash() function determines dictionary placement
print(hash("Corechunk"))
```

## 3. Portable Path (Zero-Dependency)
Standard dict access and iteration.

```python
data = {"id": 101, "active": True}
for k, v in data.items():
    print(f"{k}: {v}")
```

## 4. Strict Path (Type-Hinted)
Typed Dictionaries and Sets.

```python
from typing import Dict, Set

mapping: Dict[str, int] = {"count": 10}
unique_ids: Set[int] = {1, 2, 3}
```

# The Logic Bridge
// Logic: Python's `dict` is a highly optimized hash table. Since Python 3.7, dictionaries are officially **Ordered**, meaning they remember the insertion order of keys. This was achieved by separating the hash indices from the actual key-value storage in the C implementation.
