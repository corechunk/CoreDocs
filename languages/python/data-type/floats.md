# Floating Point (CORE)

Definition: Python floats are standard double-precision (64-bit) values following IEEE 754.

## 1. Modern Path (3.12+ / Idiomatic)
Scientific notation and basic float math.

```python
pi = 3.14159
sci = 1.2e3 # 1200.0
```

## 2. Systems Path (Internals / C-Interop)
Checking float information and precision limits.

```python
import sys
print(sys.float_info)
# Logic: Shows max/min values and epsilon (precision limit).
```

## 3. Portable Path (Zero-Dependency)
Using the `math` module for operations.

```python
import math
print(math.isclose(0.1 + 0.2, 0.3)) # Output: True
```

## 4. Strict Path (Type-Hinted)
Explicit float typing.

```python
price: float = 19.99
```

# The Logic Bridge
// Logic: A Python `float` is a wrapper around a C `double`. Because of binary floating-point representation, certain decimal values (like 0.1) cannot be represented exactly, leading to minor precision errors.
