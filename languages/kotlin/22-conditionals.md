# 22 - Conditionals (CORE - Hub)

Definition: Conditionals in Kotlin are expressions that return a value. The `if` and `when` structures are the primary tools for control flow, with `when` acting as a powerful replacement for the traditional `switch`.

## 1. JVM-Legacy (Java-Interop Style)
Using `if` as a statement.

```kotlin
fun main() {
    val score = 85
    var grade = ""
    if (score >= 90) {
        grade = "A"
    } else {
        grade = "B"
    }
    println(grade) // Output: B
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using `when` as a concise expression.

```kotlin
fun main() {
    val score = 85
    val grade = when {
        score >= 90 -> "A"
        score >= 80 -> "B"
        else -> "F"
    }
    println(grade) // Output: B
}
```

## 3. Kotlin Native (System / C-Interop)
Conditionals interacting with POSIX return codes.

```kotlin
import platform.posix.*

fun main() {
    val result = mkdir("test_dir", 0777)
    if (result == 0) {
        println("Dir created")
    } else {
        println("Error code: $errno")
    }
}
```

## 4. Multiplatform Path (KMP / Common)
Target-agnostic conditional logic.

```kotlin
fun main() {
    val list = listOf(1, 2, 3)
    val msg = if (list.isNotEmpty()) "Has Data" else "Empty"
    println(msg) // Output: Has Data
}
```

## 5. Explicit Path (Strictly Typed)
Explicitly exhaustive `when` expressions with types.

```kotlin
enum class Status { OK, ERROR }

fun main() {
    val s: Status = Status.OK
    val result: String = when (s) {
        Status.OK -> "Success"
        Status.ERROR -> "Failure"
    }
    println(result) // Output: Success
}
```

# The Logic Bridge
// Logic: Kotlin's `if` and `when` are expressions, meaning they leave a value on the stack. The `when` structure is compiled into a series of `if-else` checks or a `lookupswitch`/`tableswitch` in the JVM bytecode, depending on the complexity of the branches. In Kotlin/Native, `when` is optimized for fast branching similar to C `switch`.
