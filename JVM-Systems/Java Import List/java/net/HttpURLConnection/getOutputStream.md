# Method: getOutputStream()
## Class: `java.net.HttpURLConnection`

Returns an output stream that writes to this connection.

### Signature
- **Inputs:** None
- **Returns:** `java.io.OutputStream` — The output stream for writing the request body.

### Description
Used for POST or PUT requests to send data to the server. You must call `setDoOutput(true)` before calling this.

### Example (Kotlin)
```kotlin
conn.doOutput = true
val os = conn.outputStream
os.write(jsonData.toByteArray())
```
