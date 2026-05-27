# Method: exists()
## Class: `java.io.File`

Tests whether the file or directory denoted by this abstract pathname exists.

### Signature
- **Inputs:** None
- **Returns:** `boolean` — `true` if and only if the file or directory exists.

### Example (Kotlin)
```kotlin
val f = File("test.txt")
if (f.exists()) {
    println("File exists")
}
```
