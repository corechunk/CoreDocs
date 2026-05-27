# 42 - Error Handling (CORE)

Definition: Error handling in Python is performed using `try-except` blocks. Python encourages "EAFP" (Easier to Ask for Forgiveness than Permission).

## 1. Modern Path (3.12+ / Idiomatic)
Modern Exception Groups (3.11+) and standard handling.

```python
try:
    val = 10 / 0
except ZeroDivisionError as e:
    print(f"Caught: {e}") # Output: Caught: division by zero
```

## 2. Systems Path (Internals / C-Interop)
The `traceback` module and stack inspection.

```python
import traceback

try:
    1/0
except:
    traceback.print_exc() # Logic: Dumps the C-level stack trace
```

## 3. Portable Path (Zero-Dependency)
Using `finally` for resource cleanup.

```python
f = None
try:
    f = open("test.txt", "w")
finally:
    if f: f.close()
```

## 4. Strict Path (Type-Hinted)
Defining custom exception types.

```python
class CoreError(Exception):
    """Base error for this module."""
    pass
```

# The Logic Bridge
// Logic: Exceptions in Python are objects. When an error occurs, the VM stops the current bytecode execution and searches up the stack for a matching `except` block. If the global scope is reached without a handler, the interpreter prints the traceback and terminates the process.
