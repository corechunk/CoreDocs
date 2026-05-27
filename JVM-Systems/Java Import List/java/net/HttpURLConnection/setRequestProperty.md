# Method: setRequestProperty(String key, String value)
## Class: `java.net.HttpURLConnection`

Sets the general request property (HTTP Header).

### Signature
- **Inputs:** 
    - `key: String` — The keyword by which the request is known (e.g., "Content-Type").
    - `value: String` — The value associated with it.
- **Returns:** `void`

### Description
Use this to set headers like `Authorization`, `Accept`, or `User-Agent`.

### Example (Kotlin)
```kotlin
conn.setRequestProperty("Content-Type", "application/json")
conn.setRequestProperty("Accept", "application/json")
```
