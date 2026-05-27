# 43 - Synchronization (SYSTEMS)

Definition: Managing access to shared resources.

## 1. Modern Path (3.12+ / Idiomatic)
Locks and semaphores.

```python
import threading
lock = threading.Lock()
with lock:
    print("Critical section")
```

## 2. Systems Path (Internals / C-Interop)
Atomic operations and memory barriers in C.

```python
# Usually handled by C-extensions
```

## 3. Portable Path (Zero-Dependency)
Standard thread safety.

```python
import queue
q = queue.Queue() # Thread-safe queue
```

## 4. Strict Path (Type-Hinted)
Explicitly typed synchronization objects.

```python
from threading import Event
done: Event = Event()
```

# The Logic Bridge
// Logic: Because of the GIL, simple variable assignments in Python are often "atomic" at the bytecode level, but complex operations (like `x += 1`) require locks because the interpreter can switch threads between reading and writing the value.
