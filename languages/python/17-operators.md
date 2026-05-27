# 17 - Operators (CORE - Hub)

Definition: Operators are symbols that perform operations on values and variables. Python implements operators as "Dunder" (Double Under) methods, allowing for operator overloading.

## 1. Modern Path (3.12+ / Idiomatic)
Standard math and membership operators.

```python
x = 10 / 3  # Float division
y = 10 // 3 # Integer division (Floor)

items = [1, 2, 3]
print(1 in items) # Membership operator. Output: True
```

## 2. Systems Path (Internals / C-Interop)
Examining operators through the `operator` module and Dunder methods.

```python
import operator

# Equivalent to 10 + 5
print(operator.add(10, 5)) # Output: 15

# Operator overloading hook
# 10 + 5 calls 10.__add__(5)
```

## 3. Portable Path (Zero-Dependency)
Logical and comparison operators.

```python
a = True
b = False
print(a and b) # Output: False
print(10 != 5) # Output: True
```

## 4. Strict Path (Type-Hinted)
Performing operations on strictly typed variables.

```python
val_a: int = 10
val_b: int = 20

# Explicitly ensuring result is an integer
result: int = val_a + val_b
print(result) # Output: 30
```

# The Logic Bridge
// Logic: Operators in Python are syntactic sugar for method calls. For instance, `a + b` is translated to `a.__add__(b)`. This is a form of **Dynamic Dispatch** where the Python interpreter looks up the method in the object's type dictionary at runtime.
