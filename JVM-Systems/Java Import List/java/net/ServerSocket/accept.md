# Method: accept()
## Class: `java.net.ServerSocket`

Listens for a connection to be made to this socket and accepts it.

### Signature
- **Inputs:** None
- **Returns:** `java.net.Socket` — The new socket for the client connection.

### Description
The method **blocks** (pauses execution) until a client connects to the server. Once a connection is established, it returns a `Socket` object that you can use to communicate with that specific client.

### Example (Kotlin)
```kotlin
val server = ServerSocket(8080)
val clientSocket: Socket = server.accept() // Blocks here
```
