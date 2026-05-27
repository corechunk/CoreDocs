# 11 - Interpolation (CORE)

Definition: String interpolation is the process of evaluating a string literal containing placeholders. Python provides several ways to do this, with f-strings being the modern standard.

## 1. Modern Path (3.12+ / Idiomatic)
Using f-strings with expressions and formatting.

```python
user = "Corechunk"
val = 10.1234

# Formatting to 2 decimal places
print(f"User: {user}, Value: {val:.2f}") # Output: User: Corechunk, Value: 10.12
```

## 2. Systems Path (Internals / C-Interop)
How f-strings are compiled to bytecode instructions.

```python
import dis

def interpolate():
    x = 1
    return f"val: {x}"

dis.dis(interpolate) 
# Logic: Shows FORMAT_VALUE and BUILD_STRING bytecode instructions.
```

## 3. Portable Path (Zero-Dependency)
Using the older `.format()` method and `%` operator (Legacy but portable).

```python
user = "Old"
# Method A: .format()
print("Hello {}".format(user)) # Output: Hello Old

# Method B: % operator
print("Hex: %x" % 255) # Output: Hex: ff
```

## 4. Strict Path (Type-Hinted)
Ensuring interpolated values match expected types.

```python
user: str = "Strict"
age: int = 25

msg: str = f"{user} is {age} years old"
print(msg) # Output: Strict is 25 years old
```

# The Logic Bridge
// Logic: f-strings (introduced in 3.6) are evaluated at runtime rather than being static constants. They are faster than `%` or `.format()` because the compiler generates specialized bytecode to build the string in one pass, avoiding the overhead of the string formatting parser at execution time.
