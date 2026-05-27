# Method: readString(Path path)
## Class: `java.nio.file.Files`

Reads all content from a file into a string.

### Signature
- **Inputs:** `path: Path` — The path to the file.
- **Returns:** `String` — A string containing the file's content.

### Example (Kotlin)
```kotlin
val path = Path.of("test.txt")
val content = Files.readString(path)
```
