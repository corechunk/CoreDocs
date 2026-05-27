# Method: connect(SocketAddress endpoint)
## Class: `java.net.Socket`

Connects this socket to the server.

### Signature
- **Inputs:** `endpoint: SocketAddress` — The address and port to connect to.
- **Returns:** `void`

### Description
Connects the socket to the remote host. A timeout can optionally be specified using the overloaded `connect(endpoint, timeout)` method.

### Example (Kotlin)
```kotlin
val address = InetSocketAddress("example.com", 80)
socket.connect(address)
```
