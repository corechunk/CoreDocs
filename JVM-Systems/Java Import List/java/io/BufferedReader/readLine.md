# Method: readLine()
## Class: `java.io.BufferedReader`

Reads a line of text.

### Signature
- **Inputs:** None
- **Returns:** `String` — A String containing the contents of the line, or null if end of stream reached.

### Example (Kotlin)
```kotlin
val reader = BufferedReader(FileReader("test.txt"))
val line = reader.readLine()
```
