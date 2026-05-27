# 41 - Async & Coroutines (PRO)

Definition: Cooperative multitasking using `async`/`await`.

## 1. Modern Path (3.12+ / Idiomatic)
`asyncio` event loop.

```python
import asyncio
async def main():
    print("Async Start")
    await asyncio.sleep(1)

asyncio.run(main())
```

## 2. Systems Path (Internals / C-Interop)
Generators and the `yield from` evolution.

```python
def loop():
    yield "Step 1"
    yield "Step 2"
```

## 3. Portable Path (Zero-Dependency)
Basic generator-based coroutines.

```python
def count():
    n = 0
    while True:
        yield n
        n += 1
```

## 4. Strict Path (Type-Hinted)
Typed Coroutines and Awaitables.

```python
from typing import Coroutine
async def task() -> int: return 1
```

# The Logic Bridge
// Logic: Coroutines are functions that can be "paused" and "resumed." Under the hood, Python uses an Event Loop that tracks which coroutines are waiting for I/O and switches execution between them, allowing one thread to handle thousands of concurrent connections.
