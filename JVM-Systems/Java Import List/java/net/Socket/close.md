# Method: close()
## Class: `java.net.Socket`

Closes this socket.

### Signature
- **Inputs:** None
- **Returns:** `void`

### Description
Once a socket has been closed, it is not available for further networking use (i.e. can't be reconnected or rebound). A new socket needs to be created.

### Example (Kotlin)
```kotlin
socket.close()
```
