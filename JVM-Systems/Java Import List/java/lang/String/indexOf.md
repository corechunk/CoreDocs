# Method: indexOf(String str)
## Class: `java.lang.String`

Returns the index within this string of the first occurrence of the specified substring.

### Signature
- **Inputs:** `str: String` — Any string.
- **Returns:** `int` — The index of the first character of the substring, or -1 if it does not occur.

### Description
Search starts from the beginning of the string.

### Example (Kotlin)
```kotlin
val text = "Hello World"
val index = text.indexOf("World") // 6
```
