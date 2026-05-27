# 28 - Recursion (CORE)

Definition: A function calling itself. Python has a fixed recursion depth to prevent C-stack overflow.

## 1. Modern Path (3.12+ / Idiomatic)
Standard factorial recursion.

```python
def fact(n: int) -> int:
    return 1 if n <= 1 else n * fact(n - 1)
```

## 2. Systems Path (Internals / C-Interop)
Checking and setting the recursion limit.

```python
import sys
print(sys.getrecursionlimit()) # Default 1000
# sys.setrecursionlimit(2000)
```

## 3. Portable Path (Zero-Dependency)
Recursive search logic.

```python
def walk(tree):
    for node in tree:
        if isinstance(node, list): walk(node)
```

## 4. Strict Path (Type-Hinted)
Explicitly typed recursive calls.

```python
def fib(n: int) -> int:
    if n <= 1: return n
    return fib(n-1) + fib(n-2)
```

# The Logic Bridge
// Logic: Unlike Kotlin or Scheme, Python does **not** perform Tail-Call Optimization (TCO). Every recursive call creates a new Frame object in memory. This is why the recursion limit exists—to protect the OS memory from being exhausted by infinite recursive loops.
