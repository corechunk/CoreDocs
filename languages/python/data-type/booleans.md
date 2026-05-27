# Booleans (CORE)

Definition: `bool` represents truth values `True` and `False`. In Python, `bool` is a subclass of `int`.

## 1. Modern Path (3.12+ / Idiomatic)
Logical evaluation.

```python
is_valid = True
check = 10 > 5
```

## 2. Systems Path (Internals / C-Interop)
Boolean-to-Integer mapping.

```python
print(int(True))  # Output: 1
print(int(False)) # Output: 0
print(True + True) # Output: 2
# Logic: Booleans are stored as integers 1 and 0 in CPython.
```

## 3. Portable Path (Zero-Dependency)
Truthiness checks (Implicit Booleans).

```python
empty_list = []
if not empty_list:
    print("Empty") # Output: Empty
```

## 4. Strict Path (Type-Hinted)
Explicit boolean typing.

```python
is_active: bool = False
```

# The Logic Bridge
// Logic: While Python supports "Truthiness" (where 0, [], None are false), the `bool` type itself is a strict binary state. Historically, `True` and `False` were added late to Python, which is why they still behave like the integers 1 and 0 for backward compatibility.
