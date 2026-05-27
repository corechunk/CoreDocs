# Method: setRequestMethod(String method)
## Class: `java.net.HttpURLConnection`

Sets the method for the URL request (GET, POST, etc.).

### Signature
- **Inputs:** `method: String` — The HTTP method (e.g., "GET", "POST", "PUT").
- **Returns:** `void` — Modifies the connection state in place.

### Description
This method must be called before the connection is established. It determines what kind of action the request will perform on the server.

### Example (Kotlin)
```kotlin
val conn = url.openConnection() as HttpURLConnection
conn.requestMethod = "POST"
```
