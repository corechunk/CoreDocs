# Method: getInputStream()
## Class: `java.net.Socket`

Returns an input stream for this socket.

### Signature
- **Inputs:** None
- **Returns:** `java.io.InputStream` — A stream to read data coming from the remote connection.

### Description
Use this method to get a stream that allows you to read data sent by the other side of the connection (e.g., the server or the client). Usually wrapped in a `BufferedReader` for easier text reading.

### Example (Kotlin)
```kotlin
val socket = Socket("example.com", 80)
val inputStream: InputStream = socket.getInputStream()
val reader = inputStream.bufferedReader()
val firstLine = reader.readLine()
```
