# 26 - Function Basics (CORE)

Definition: Functions are modular, reusable blocks of code. Python functions are first-class objects, meaning they can be passed as arguments, returned from other functions, and assigned to variables.

## 1. Modern Path (3.12+ / Idiomatic)
Defining functions with default arguments and docstrings.

```python
def greet(name: str = "Guest") -> str:
    """Returns a greeting string."""
    return f"Hello, {name}"

print(greet("Corechunk")) # Output: Hello, Corechunk
```

## 2. Systems Path (Internals / C-Interop)
Examining function objects and their `__code__` attributes.

```python
def func(x): return x + 1

print(func.__code__.co_argcount) # Output: 1
print(func.__code__.co_varnames) # Output: ('x',)
# Logic: Shows how the VM stores function metadata.
```

## 3. Portable Path (Zero-Dependency)
Using `*args` and `**kwargs` for flexible parameter handling.

```python
def multi_log(*args, **kwargs):
    prefix = kwargs.get("prefix", "LOG")
    for arg in args:
        print(f"[{prefix}]: {arg}")

multi_log("Startup", "Init", prefix="SYS")
# Output: [SYS]: Startup, [SYS]: Init
```

## 4. Strict Path (Type-Hinted)
Explicitly defining all types and using `Callable`.

```python
from typing import Callable

def executor(func: Callable[[int], int], value: int) -> int:
    return func(value)

result: int = executor(lambda x: x * 2, 10)
print(result) # Output: 20
```

# The Logic Bridge
// Logic: At the C-layer, every Python function is an instance of `PyFunctionObject`. When a function is called, the VM creates a new **Frame Object** on the execution stack. Python 3.11+ uses "Specialized Adaptive Interpreters" to optimize function calls by caching frequently used method lookups.
