# 39 - Process Forking (SYSTEMS)

Definition: Spawning independent OS processes.

## 1. Modern Path (3.12+ / Idiomatic)
The `multiprocessing` module for bypassing the GIL.

```python
from multiprocessing import Process
def task(): print("Child")

p = Process(target=task)
p.start()
p.join()
```

## 2. Systems Path (Internals / C-Interop)
Direct OS `fork` calls (Unix only).

```python
import os
pid = os.fork()
if pid == 0:
    print("In child")
    os._exit(0)
```

## 3. Portable Path (Zero-Dependency)
Basic `os.system` process spawning.

```python
import os
os.system("echo Hello")
```

## 4. Strict Path (Type-Hinted)
Managing process state with types.

```python
from multiprocessing import Process
p: Process = Process()
```

# The Logic Bridge
// Logic: `fork()` creates a copy-on-write clone of the entire parent process memory. Since Python has a Global Interpreter Lock (GIL), true CPU parallelism can only be achieved by spawning multiple processes, each with its own private VM and memory space.
