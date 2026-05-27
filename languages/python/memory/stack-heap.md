# 46 - Stack vs Heap (SYSTEMS)

Definition: Python allocates almost everything on the **Heap**. The "Stack" primarily stores pointers to these heap objects.

## 1. Modern Path (3.12+ / Idiomatic)
Function call frames.

```python
def call():
    x = 1 # Pointer on stack, object on heap
```

## 2. Systems Path (Internals / C-Interop)
Accessing frame objects.

```python
import sys
frame = sys._getframe()
print(frame.f_locals)
```

## 3. Portable Path (Zero-Dependency)
Managing deep stacks.

```python
import sys
sys.setrecursionlimit(1000)
```

## 4. Strict Path (Type-Hinted)
Explicitly avoiding large stack frame creations.

```python
def flat_logic():
    data = [i for i in range(1000)]
```

# The Logic Bridge
// Logic: In C-languages, local primitives are on the stack. In Python, even an `int` is a `PyObject` allocated via `malloc` on the heap. The "Stack" in Python is an array of `PyFrameObject` pointers maintained by the VM.
