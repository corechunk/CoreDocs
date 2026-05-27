# 22 - Truth Rule (CORE)

Definition: In Kotlin, Booleans are strict. Unlike C or Bash, there is no "Truthiness" for integers or strings. Only the `Boolean` values `true` and `false` can be used in conditional contexts.2

## 1. JVM-Legacy (Java-Interop Style)
Strict Boolean logic as required by the JVM.

```kotlin
fun main() {
    val isActive = true
    if (isActive) {
        println("Active") // Output: Active
    }
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Explicitly checking conditions to generate Booleans.

```kotlin
fun main() {
    val count = 0
    // if (count) { } // Error: Type mismatch
    if (count != 0) {
        println("Has items")
    } else {
        println("Empty") // Output: Empty
    }
}
```

## 3. Multiplatform Path (KMP / Common)
Strict Boolean rules apply to all Kotlin targets.

```kotlin
fun main() {
    val list = emptyList<String>()
    if (list.isEmpty()) {
        println("Common Empty") // Output: Common Empty
    }
}
```

## 4. Explicit Path (Strictly Typed)
Comparing objects explicitly to get a Boolean result.

```kotlin
fun main() {
    val name: String? = null
    val result: Boolean = name?.isNotEmpty() == true
    
    println(result) // Output: false
}
```

# The Logic Bridge
// Logic: Kotlin avoids the ambiguity of "Truthiness" (where 0 or "" might be false) to ensure type safety. At the JVM level, `Boolean` is represented as an `int` (1 for true, 0 for false), but the Kotlin compiler enforces that only actual Boolean expressions are valid in control flow structures.
