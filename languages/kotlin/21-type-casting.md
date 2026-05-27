# 21 - Type Casting (CORE)

Definition: Type casting is the process of converting a variable from one type to another. Kotlin provides "Smart Casts" which automatically cast a variable after a type check (`is`).

## 1. JVM-Legacy (Java-Interop Style)
Manual casting using the `as` operator (Unsafe cast).

```kotlin
fun main() {
    val obj: Any = "Kotlin"
    // Java Style: (String) obj
    val str = obj as String
    println(str.length) // Output: 6
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using Smart Casts with the `is` check.

```kotlin
fun main() {
    val obj: Any = "Kotlin"
    
    if (obj is String) {
        // Automatically cast to String inside this block
        println(obj.length) // Output: 6
    }
}
```

## 3. Multiplatform Path (KMP / Common)
Smart casts are a compiler feature available on all platforms.

```kotlin
fun check(x: Any) {
    if (x !is String) return
    println(x.uppercase())
}

fun main() {
    check("kmp") // Output: KMP
}
```

## 4. Explicit Path (Strictly Typed)
Using the "Safe Cast" operator `as?` which returns `null` on failure.

```kotlin
fun main() {
    val obj: Any = 123
    val str: String? = obj as? String
    
    println(str) // Output: null
}
```

# The Logic Bridge
// Logic: Kotlin's Smart Cast feature is powered by the compiler's Data Flow Analysis. Once a type check (`is`) or null check (`!= null`) is performed, the compiler tracks that the variable's type is restricted within that specific control flow branch. In Kotlin 2.0 (K2), this analysis is even more robust, handling complex scenarios like property delegation and cross-module checks.
