# Method: getResponseCode()
## Class: `java.net.HttpURLConnection`

Gets the status code from an HTTP response message.

### Signature
- **Inputs:** None
- **Returns:** `int` — The HTTP status code (e.g., 200 for OK, 404 for Not Found).

### Description
Calling this method will trigger the actual network request if it hasn't been sent yet. It is the standard way to check if your API call was successful.

### Example (Kotlin)
```kotlin
val status = conn.responseCode
if (status == 200) {
    println("Success!")
}
```
