# 12 - Scope & Lifetime (CORE)

Definition: The LEGB rule (Local, Enclosing, Global, Built-in) defines name resolution.

## 1. Modern Path (3.12+ / Idiomatic)
Function scoping.

```python
def outer():
    x = 1
    def inner(): print(x)
    inner()
```

## 2. Systems Path (Internals / C-Interop)
Using `locals()` and `globals()` dictionaries.

```python
print(locals().keys())
```

## 3. Portable Path (Zero-Dependency)
Global modification.

```python
count = 0
def inc():
    global count
    count += 1
```

## 4. Strict Path (Type-Hinted)
Nonlocal scope for closures.

```python
def counter():
    x = 0
    def inc():
        nonlocal x
        x += 1
        return x
    return inc
```

# The Logic Bridge
// Logic: Scoping is implemented via Hash Maps (namespaces). Every module, class, and function has its own `__dict__`. Variable lifetime is tied to the reference count of the object; when it hits zero, the memory is reclaimed.
