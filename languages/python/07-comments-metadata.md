# 07 - Comments & Metadata (CORE)

Definition: Documentation and metadata.

## 1. Modern Path (3.12+ / Idiomatic)
Docstrings with type info.

```python
def run(x: int):
    """
    Execute task.
    :param x: ID
    """
```

## 2. Systems Path (Internals / C-Interop)
Inspecting `__doc__` and `__annotations__`.

```python
print(run.__doc__)
print(run.__annotations__)
```

## 3. Portable Path (Zero-Dependency)
Single line comments.

```python
# System config
PORT = 80
```

## 4. Strict Path (Type-Hinted)
PEP 484 type comments (Legacy but strict).

```python
x = 1 # type: int
```

# The Logic Bridge
// Logic: Docstrings are stored in the object's `__doc__` attribute and remain available at runtime, unlike standard comments which are stripped during the tokenization phase.
