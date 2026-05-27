# 22 - Truth Rule (CORE)

Definition: Python evaluates objects in a Boolean context using the "Truthiness" rules.

## 1. Modern Path (3.12+ / Idiomatic)
Explicitly checking for empty collections.

```python
items = []
if not items:
    print("Empty") # Output: Empty
```

## 2. Systems Path (Internals / C-Interop)
The `__bool__` and `__len__` methods.

```python
class Custom:
    def __bool__(self): return False

c = Custom()
print(bool(c)) # Output: False
```

## 3. Portable Path (Zero-Dependency)
Zero-parity and None checks.

```python
if 0: print("True") # Fails
if None: print("True") # Fails
```

## 4. Strict Path (Type-Hinted)
Enforcing strict boolean results.

```python
val: int = 1
is_set: bool = val != 0
```

# The Logic Bridge
// Logic: Python checks truthiness by first looking for a `__bool__` method. If missing, it checks `__len__`. An object is False if `bool(obj)` returns False or `len(obj)` returns 0. Otherwise, it is True.
