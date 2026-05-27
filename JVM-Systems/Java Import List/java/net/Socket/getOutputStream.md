# Method: getOutputStream()
## Class: `java.net.Socket`

Returns an output stream for this socket.

### Signature
- **Inputs:** None
- **Returns:** `java.io.OutputStream` — A stream to write data to the remote connection.

### Description
Use this method to get a stream that allows you to send data to the other side of the connection. Often used to send requests or data packets.

### Example (Kotlin)
```kotlin
val socket = Socket("example.com", 80)
val outputStream: OutputStream = socket.getOutputStream()
outputStream.write("Hello Server".toByteArray())
```
