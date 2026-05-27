# Bitwise Operators (CORE)

Definition: Operators that manipulate data at the bit level inside integer objects.

## 1. Modern Path (3.12+ / Idiomatic)
Standard shifting and logical bit operations.

```python
x = 1 << 3 # Shift left (multiply by 2^3)
mask = 0b1010 & 0b1100 # AND
print(bin(mask)) # Output: 0b1000
```

## 2. Systems Path (Internals / C-Interop)
Using bitwise logic to parse C-style flags.

```python
import os
# Bitwise OR to combine flags
flags = os.O_RDWR | os.O_CREAT
```

## 3. Portable Path (Zero-Dependency)
Inversion and XOR.

```python
print(~1) # -2 (Two's complement)
print(5 ^ 3) # XOR logic
```

## 4. Strict Path (Type-Hinted)
Ensuring bitwise operations are performed on integers.

```python
val: int = 0xFF
res: int = val >> 4
```

# The Logic Bridge
// Logic: Python handles bitwise operations by treating the arbitrary-precision integer as if it were a two's complement binary string of infinite length, ensuring consistent behavior even with extremely large bitsets.
