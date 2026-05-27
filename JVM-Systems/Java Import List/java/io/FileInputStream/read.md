# Method: read()
## Class: `java.io.FileInputStream`

Reads a byte of data from this input stream.

### Signature
- **Inputs:** None
- **Returns:** `int` — The next byte of data, or -1 if the end of the file is reached.

### Example (Kotlin)
```kotlin
val fis = FileInputStream("test.txt")
val data = fis.read()
```
