# 08 - Variables & Constants (CORE)

Definition: In Kotlin, variable declaration is centered around mutability. `val` defines a read-only (immutable) reference, while `var` defines a mutable one. For compile-time constants, `const val` is used. Kotlin/Native adds unique behaviors for memory sharing across threads.

## 1. JVM-Legacy (Java-Interop Style)
Traditional Java-like declarations.

```kotlin
// Java equivalent: final String user = "Corechunk";
val user: String = "Corechunk"

// Java equivalent: int count = 5;
var count: Int = 5

fun main() {
    println(user)  // Output: Corechunk
    println(count) // Output: 5
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Concise syntax with type inference.

```kotlin
val user = "Corechunk" 
var count = 5

fun main() {
    count += 1
    println("$user: $count") // Output: Corechunk: 6
}
```

## 3. Kotlin Native (System / C-Interop)
Using C-interop to access native memory or POSIX constants.

```kotlin
import platform.posix.*

fun main() {
    // Accessing a C global/constant via POSIX
    val pid = getpid()
    println("Native Process ID: $pid") // Output: Native Process ID: [Current PID]
}
```

## 4. Multiplatform Path (KMP / Common)
Target-agnostic declarations.

```kotlin
const val MAX_RETRIES = 10

fun main() {
    val platform = "Common"
    println("$platform Max: $MAX_RETRIES") // Output: Common Max: 10
}
```

## 5. Explicit Path (Strictly Typed)
Manual typing to remove all ambiguity.

```kotlin
const val ID: Int = 100

fun main() {
    val name: String = "Corechunk"
    var score: Int = 0
    
    score = score + 10
    println("${name} score: ${score}") // Output: Corechunk score: 10
}
```

# The Logic Bridge
// Logic: At the bytecode level, `val` maps to a Java `final` field. In Kotlin/Native, `val` objects are by default strictly tied to the thread that created them (unless made immutable or frozen in older versions), preventing data races at the architectural level. `const val` is handled at compile-time, with the value inlined directly into the calling code.
