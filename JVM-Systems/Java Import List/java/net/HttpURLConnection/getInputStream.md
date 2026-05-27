# Method: getInputStream()
## Class: `java.net.HttpURLConnection`

Returns an input stream that reads from this open connection.

### Signature
- **Inputs:** None
- **Returns:** `java.io.InputStream` — The input stream for reading the response body.

### Description
Throws an `IOException` if the server returns an error code (4xx or 5xx). In those cases, use `getErrorStream()` instead.

### Example (Kotlin)
```kotlin
val stream = conn.inputStream
val result = stream.bufferedReader().readText()
```
