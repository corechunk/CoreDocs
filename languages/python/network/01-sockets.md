# 49 - Socket Basics (SYSTEMS)

Definition: Network communication using the `socket` API.

## 1. Modern Path (3.12+ / Idiomatic)
`asyncio` streams for networking.

```python
import asyncio
async def tcp_echo():
    reader, writer = await asyncio.open_connection('127.0.0.1', 8888)
```

## 2. Systems Path (Internals / C-Interop)
The `socket` module (thin wrapper over POSIX).

```python
import socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(("127.0.0.1", 80))
```

## 3. Portable Path (Zero-Dependency)
Standard blocking sockets.

```python
import socket
# s.send(b"GET / HTTP/1.0\r\n\r\n")
```

## 4. Strict Path (Type-Hinted)
Explicitly typed socket objects.

```python
from socket import socket as SocketObj
s: SocketObj = SocketObj()
```

# The Logic Bridge
// Logic: Python's `socket` module is a direct mapping of the BSD sockets API. When you create a socket, the OS returns a file descriptor which Python stores in a `PySocketSockObject` structure.
