# Method: nextInt(int bound)
## Class: `java.util.Random`

Returns a pseudorandom, uniformly distributed int value between 0 (inclusive) and the specified value (exclusive).

### Signature
- **Inputs:** `bound: int` — The upper bound (exclusive).
- **Returns:** `int` — The random value.

### Example (Kotlin)
```kotlin
val rand = Random()
val num = rand.nextInt(100) // 0-99
```
