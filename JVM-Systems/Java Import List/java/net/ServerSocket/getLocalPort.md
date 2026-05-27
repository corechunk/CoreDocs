# Method: getLocalPort()
## Class: `java.net.ServerSocket`

Returns the port number on which this socket is listening.

### Signature
- **Inputs:** None
- **Returns:** `int` — The port number.

### Description
Useful if you initialized the `ServerSocket` with port 0 (which tells the OS to pick any free port).

### Example (Kotlin)
```kotlin
val server = ServerSocket(0)
val port = server.localPort
println("Server started on port $port")
```
