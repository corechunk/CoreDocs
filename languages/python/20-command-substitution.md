# 20 - Command Substitution (PRO)

Definition: Executing external OS commands and capturing their output. In Python, this is handled by the `subprocess` module.

## 1. Modern Path (3.12+ / Idiomatic)
Using `subprocess.run` with text capturing.

```python
import subprocess
res = subprocess.run(["ls", "-l"], capture_output=True, text=True)
print(res.stdout)
```

## 2. Systems Path (Internals / C-Interop)
Interacting with OS file descriptors via `os.popen`.

```python
import os
pipe = os.popen("echo Hello")
print(pipe.read())
```

## 3. Portable Path (Zero-Dependency)
Basic execution with `os.system` (No capture).

```python
import os
os.system("clear")
```

## 4. Strict Path (Type-Hinted)
Explicitly typed result handling.

```python
from subprocess import CompletedProcess
result: CompletedProcess = subprocess.run(["whoami"], capture_output=True)
```

# The Logic Bridge
// Logic: `subprocess` uses the `fork()` and `exec()` system calls on Unix to create child processes. The `capture_output` flag tells the Kernel to pipe the child's `stdout` and `stderr` back to the parent process's memory space.
