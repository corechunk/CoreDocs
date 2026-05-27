# Method: exists(Path path)
## Class: `java.nio.file.Files`

Tests whether a file exists.

### Signature
- **Inputs:** `path: Path` — The path to the file.
- **Returns:** `boolean` — `true` if the file exists.

### Example (Kotlin)
```kotlin
if (Files.exists(Path.of("test.txt"))) { ... }
```
