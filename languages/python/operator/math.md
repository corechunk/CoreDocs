# Math Operators (CORE)

Definition: Standard arithmetic operators implemented via Dunder methods.

## 1. Modern Path (3.12+ / Idiomatic)
Exponentiation and floor division.

```python
x = 2 ** 3 # 8 (Power)
y = 7 // 2 # 3 (Floor division)
```

## 2. Systems Path (Internals / C-Interop)
Floating-point rounding and binary representation.

```python
import math
print(math.floor(3.9)) # Output: 3
```

## 3. Portable Path (Zero-Dependency)
Standard math.

```python
res = (10 + 5) * 2
```

## 4. Strict Path (Type-Hinted)
Ensuring numeric types in operations.

```python
a: int = 10
b: float = 2.5
res: float = a * b
```

# The Logic Bridge
// Logic: Arithmetic in Python is polymorphic. `a * b` works on numbers, but also strings (`"A" * 3` -> `"AAA"`). This is achieved by the VM checking the `tp_as_number` or `tp_as_sequence` slots in the object's C structure.
