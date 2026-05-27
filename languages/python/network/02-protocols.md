# 50 - Protocols: TCP & UDP (SYSTEMS)

Definition: Building servers and clients.

## 1. Modern Path (3.12+ / Idiomatic)
Modern TCP Server with `asyncio`.

```python
import asyncio
async def handler(r, w): pass
# server = await asyncio.start_server(handler, '127.0.0.1', 8888)
```

## 2. Systems Path (Internals / C-Interop)
Raw UDP packets.

```python
import socket
s = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
s.sendto(b"data", ("127.0.0.1", 9999))
```

## 3. Portable Path (Zero-Dependency)
Standard Library `http.server` for TCP.

```python
from http.server import HTTPServer, BaseHTTPRequestHandler
```

## 4. Strict Path (Type-Hinted)
Typed protocol handlers.

```python
async def serve() -> None: pass
```

# The Logic Bridge
// Logic: TCP provides a reliable, ordered byte stream via the 3-way handshake. UDP provides unreliable datagrams with zero overhead. Python handles the buffering and retransmission state machines at the C-level.
