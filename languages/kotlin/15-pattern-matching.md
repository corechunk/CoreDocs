# 15 - Pattern Matching (PRO)

Definition: Pattern matching in Kotlin is implemented through the `when` expression, which can match against types, ranges, and arbitrary conditions.

## 1. JVM-Legacy (Java-Interop Style)
Traditional `switch` or `instanceof` checks.

```kotlin
fun main() {
    val x: Any = 10
    if (x is Int) {
        println("Is Int") // Output: Is Int
    }
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Exhaustive pattern matching with `when`.

```kotlin
fun main() {
    val x: Any = "Kotlin"
    when (x) {
        is String -> println("Length: ${x.length}") // Output: Length: 6
        is Int -> println("Value: $x")
        else -> println("Unknown")
    }
}
```

## 3. Kotlin Native (System / C-Interop)
Pattern matching on native return codes or types.

```kotlin
fun main() {
    val res = 0
    when (res) {
        0 -> println("OK") // Output: OK
        else -> println("Error")
    }
}
```

## 4. Multiplatform Path (KMP / Common)
Common matching logic.

```kotlin
fun main() {
    val list = listOf(1, 2)
    when {
        list.isEmpty() -> println("Empty")
        else -> println("Has Data") // Output: Has Data
    }
}
```

## 5. Explicit Path (Strictly Typed)
Matching against sealed classes (The most robust form).

```kotlin
sealed class Result {
    object Success : Result()
    object Failure : Result()
}

fun main() {
    val r: Result = Result.Success
    val msg: String = when (r) {
        is Result.Success -> "Success"
        is Result.Failure -> "Failure"
    }
    println(msg) // Output: Success
}
```

# The Logic Bridge
// Logic: Kotlin's pattern matching via `when` is more flexible than Java's `switch` as it doesn't require constant values. When matching against `sealed class` or `enum`, the compiler performs an **Exhaustiveness Check**, ensuring all possible subclasses or cases are handled, significantly reducing runtime errors.
