# Method: ready()
## Class: `java.io.BufferedReader`

Tells whether this stream is ready to be read.

### Signature
- **Inputs:** None
- **Returns:** `boolean` — `true` if the next read() is guaranteed not to block for input.

### Example (Kotlin)
```kotlin
if (reader.ready()) { ... }
```
