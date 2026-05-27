# 14 - Native Strings (PRO)

Definition: Native strings in Kotlin refer to specialized string handling like raw strings and efficient slicing/parsing without creating excessive temporary objects.

## 1. JVM-Legacy (Java-Interop Style)
Using `substring` and concatenation.

```kotlin
fun main() {
    val s = "Kotlin"
    val sub = s.substring(0, 3)
    println(sub) // Output: Kot
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using `take`, `drop`, and `trimIndent`.

```kotlin
fun main() {
    val s = "Kotlin"
    println(s.take(3)) // Output: Kot
    println(s.drop(3)) // Output: lin
}
```

## 3. Kotlin Native (System / C-Interop)
Interacting with C-strings (`char*`).

```kotlin
import kotlinx.cinterop.*

fun main() {
    val cStr = "Native".cstr
    // println(cStr.toKString())
}
```

## 4. Multiplatform Path (KMP / Common)
String manipulation available in `commonMain`.

```kotlin
fun main() {
    val s = "KMP"
    println(s.reversed()) // Output: PMK
}
```

## 5. Explicit Path (Strictly Typed)
Explicitly using `CharSequence` for abstract handling.

```kotlin
fun process(s: CharSequence) {
    println(s.length)
}

fun main() {
    process("Strict") // Output: 6
}
```

# The Logic Bridge
// Logic: Kotlin strings are immutable. Every transformation typically creates a new `String` object. In Kotlin/Native, `.cstr` converts a Kotlin `String` (UTF-16) to a C-compatible `char*` (UTF-8) by copying the data into the native heap or a scoped memory block.
