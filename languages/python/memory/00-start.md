# 45 - Memory Management (SYSTEMS)

Definition: Reference counting and Garbage Collection (GC).

## 1. Modern Path (3.12+ / Idiomatic)
Weak references to avoid cycles.

```python
import weakref
class Data: pass
obj = Data()
r = weakref.ref(obj)
```

## 2. Systems Path (Internals / C-Interop)
Checking reference counts.

```python
import sys
x = []
print(sys.getrefcount(x)) # Output: 2 (x + argument to function)
```

## 3. Portable Path (Zero-Dependency)
Standard GC usage.

```python
import gc
gc.collect() # Force collection
```

## 4. Strict Path (Type-Hinted)
Managing object lifetime via Context Managers.

```python
class Managed:
    def __enter__(self): return self
    def __exit__(self, *args): pass
```

# The Logic Bridge
// Logic: CPython primarily uses **Reference Counting**. When `ob_refcnt` hits zero, the object is immediately deallocated. To handle circular references (e.g., A points to B and B points to A), Python has a secondary **Generational Garbage Collector** that scans for cycles periodically.
