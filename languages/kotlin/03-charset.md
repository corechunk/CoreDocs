# 03 - Charset (SYSTEMS)

Definition: Charset determines how characters are represented in memory. Kotlin handles characters as UTF-16 on the JVM and typically UTF-8 in Native environments.

## 1. JVM-Legacy (Java-Interop Style)
Standard UTF-16 character representation.

```kotlin
fun main() {
    val c: Char = 'A'
    println("Char: $c") // Output: Char: A
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Handling strings as sequences of Unicode characters.

```kotlin
fun main() {
    val emoji = "🚀"
    println("Emoji length: ${emoji.length}") // Output: Emoji length: 2 (Surrogate pairs)
}
```

## 3. Kotlin Native (System / C-Interop)
Dealing with UTF-8 strings in native interop.

```kotlin
import kotlinx.cinterop.*

fun main() {
    val nativeStr = "Native".cstr
    println("Native Pointer: $nativeStr")
}
```

## 4. Multiplatform Path (KMP / Common)
Portable character handling.

```kotlin
fun main() {
    val text = "Common"
    println(text.all { it.isLetter() }) // Output: true
}
```

## 5. Explicit Path (Strictly Typed)
Explicitly defining character encoding.

```kotlin
fun main() {
    val bytes: ByteArray = "UTF8".toByteArray(Charsets.UTF_8)
    println(bytes.size) // Output: 4
}
```

# The Logic Bridge
// Logic: On the JVM, `Char` is a 16-bit Unicode character. In Kotlin/Native, while `String` remains UTF-16 internally for consistency, interop with C libraries often requires conversion to UTF-8 using `.cstr` or `.toKString()`.
