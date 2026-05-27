# Method: substring(int beginIndex, int endIndex)
## Class: `java.lang.String`

Returns a string that is a substring of this string.

### Signature
- **Inputs:** 
    - `beginIndex: int` — The beginning index, inclusive.
    - `endIndex: int` — The ending index, exclusive.
- **Returns:** `java.lang.String` — The specified substring.

### Description
The substring begins at the specified `beginIndex` and extends to the character at index `endIndex - 1`. Thus the length of the substring is `endIndex - beginIndex`.

### Example (Kotlin)
```kotlin
val text = "Hello World"
val sub = text.substring(0, 5) // "Hello"
```
