# 27 - Return Types (CORE)

Definition: Every function in Kotlin returns a value. If no explicit return type is specified, it returns `Unit`. The `Nothing` type is used for functions that never return (e.g., those that always throw an exception).

## 1. JVM-Legacy (Java-Interop Style)
Explicit return types matching Java equivalents.

```kotlin
fun getVersion(): Int {
    return 2
}

fun main() {
    println(getVersion()) // Output: 2
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Inferred return types for single-expression functions.

```kotlin
fun isReady() = true // Infers Boolean

fun main() {
    if (isReady()) println("Ready") // Output: Ready
}
```

## 3. Kotlin Native (System / C-Interop)
Functions returning POSIX types or handles.

```kotlin
import platform.posix.*

fun getCurrentTime(): Long {
    return time(null)
}

fun main() {
    println(getCurrentTime()) // Output: [Timestamp]
}
```

## 4. Multiplatform Path (KMP / Common)
Using `Unit` and `Nothing` in shared code.

```kotlin
fun fail(msg: String): Nothing {
    throw IllegalArgumentException(msg)
}

fun main() {
    println("Running...")
    // fail("Stop") // Unreachable code after this
}
```

## 5. Explicit Path (Strictly Typed)
Explicitly declaring `Unit` for side-effect functions.

```kotlin
fun process(): Unit {
    val x: Int = 10
    println(x)
}

fun main(): Unit {
    process() // Output: 10
}
```

# The Logic Bridge
// Logic: `Unit` in Kotlin is a real object (singleton), unlike `void` in Java which is a keyword. This allows `Unit` to be used in generics. `Nothing` is a special type that has no instances and is used by the compiler to mark unreachable code paths and handle non-terminating functions.
