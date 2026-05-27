# Method: of(String first, String... more)
## Class: `java.nio.file.Path`

Returns a `Path` by converting a path string, or a sequence of strings that when joined form a path string.

### Signature
- **Inputs:** `first: String`, `more: String...`
- **Returns:** `Path` — The resulting path.

### Example (Kotlin)
```kotlin
val path = Path.of("src", "main", "resources")
```
