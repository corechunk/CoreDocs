# 44 - Exit Codes & Signals (SYSTEMS)

Definition: Process termination and signal handling.

## 1. Modern Path (3.12+ / Idiomatic)
Standard exit logic.

```python
import sys
if __name__ == "__main__":
    sys.exit(0) # 0 = Success
```

## 2. Systems Path (Internals / C-Interop)
Handling POSIX signals (SIGINT, SIGTERM).

```python
import signal
import sys

def handler(sig, frame):
    print("Caught SIGINT")
    sys.exit(0)

signal.signal(signal.SIGINT, handler)
```

## 3. Portable Path (Zero-Dependency)
The `quit()` and `exit()` built-ins (Interpreted mode only).

```python
# exit()
```

## 4. Strict Path (Type-Hinted)
Custom exit statuses.

```python
from enum import IntEnum
class ExitCode(IntEnum): OK = 0
sys.exit(ExitCode.OK)
```

# The Logic Bridge
// Logic: `sys.exit(n)` works by raising a `SystemExit` exception. If not caught, the VM terminates and returns the integer `n` to the OS as the process exit status.
