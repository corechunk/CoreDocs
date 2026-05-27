# 40 - Multi-Threading (SYSTEMS)

Definition: Concurrent execution within a single process.

## 1. Modern Path (3.12+ / Idiomatic)
The `threading` module and thread pools.

```python
import threading
def run(): print("Thread")
t = threading.Thread(target=run)
t.start()
```

## 2. Systems Path (Internals / C-Interop)
The Global Interpreter Lock (GIL) reality.

```python
import sys
# sys.setcheckinterval is legacy, now handled by 
# the interpreter's internal timer.
```

## 3. Portable Path (Zero-Dependency)
Basic thread logic.

```python
from threading import Lock
l = Lock()
```

## 4. Strict Path (Type-Hinted)
Explicitly typed threading.

```python
from threading import Thread
worker: Thread = Thread(target=run)
```

# The Logic Bridge
// Logic: Python threads are real OS threads, but the GIL ensures that only one thread can execute Python bytecode at a time. This makes threading ideal for I/O-bound tasks (waiting for network/disk), but useless for CPU-bound tasks.
