# Method: get(int index)
## Class: `java.util.ArrayList`

Returns the element at the specified position in this list.

### Signature
- **Inputs:** `index: int` — Index of the element to return.
- **Returns:** `E` — The element at the specified position in this list.

### Description
Throws `IndexOutOfBoundsException` if the index is out of range (`index < 0 || index >= size()`).

### Example (Kotlin)
```kotlin
val item = list.get(0)
// or using Kotlin syntax
val item = list[0]
```
