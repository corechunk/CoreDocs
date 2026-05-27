# Method: write(int b)
## Class: `java.io.FileOutputStream`

Writes the specified byte to this file output stream.

### Signature
- **Inputs:** `b: int` — The byte to be written.
- **Returns:** `void`

### Example (Kotlin)
```kotlin
val fos = FileOutputStream("test.txt")
fos.write(65)
```
