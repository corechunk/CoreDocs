# Method: writeString(Path path, CharSequence csq)
## Class: `java.nio.file.Files`

Write a `CharSequence` to a file.

### Signature
- **Inputs:** 
    - `path: Path` — The path to the file.
    - `csq: CharSequence` — The characters to write.
- **Returns:** `Path` — The path to the file.

### Example (Kotlin)
```kotlin
Files.writeString(Path.of("test.txt"), "Hello")
```
