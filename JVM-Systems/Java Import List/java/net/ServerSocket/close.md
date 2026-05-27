# Method: close()
## Class: `java.net.ServerSocket`

Closes this socket.

### Signature
- **Inputs:** None
- **Returns:** `void`

### Description
Any thread currently blocked in `accept()` will throw a `SocketException`.

### Example (Kotlin)
```kotlin
serverSocket.close()
```
