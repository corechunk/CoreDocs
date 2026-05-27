# Method: replace(CharSequence target, CharSequence replacement)
## Class: `java.lang.String`

Replaces each substring of this string that matches the literal target sequence with the specified literal replacement sequence.

### Signature
- **Inputs:** 
    - `target: CharSequence` — The sequence of characters to be replaced.
    - `replacement: CharSequence` — The replacement sequence of characters.
- **Returns:** `java.lang.String` — The resulting string.

### Description
The replacement proceeds from the beginning of the string to the end.

### Example (Kotlin)
```kotlin
val text = "Hello World"
val newText = text.replace("World", "Kotlin") // "Hello Kotlin"
```
