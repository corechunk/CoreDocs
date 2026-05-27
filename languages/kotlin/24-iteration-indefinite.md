# 24 - Iteration: Indefinite (CORE)

Definition: Indefinite iteration is used when the number of cycles is unknown and depends on a condition. Kotlin supports `while` and `do-while` loops.

## 1. JVM-Legacy (Java-Interop Style)
Standard `while` loop logic.

```kotlin
fun main() {
    var i = 3
    while (i > 0) {
        print("$i ")
        i--
    }
    // Output: 3 2 1 
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using `do-while` for "at-least-once" execution.

```kotlin
fun main() {
    var i = 0
    do {
        print("$i ")
        i++
    } while (i < 0) // Executes once despite condition
    // Output: 0 
}
```

## 3. Kotlin Native (System / C-Interop)
Looping until a C function returns a specific state (e.g., NULL).

```kotlin
import platform.posix.*

fun main() {
    // Simulated C-style loop (pseudo)
    var count = 0
    while (count < 2) {
        usleep(1000u) // Native micro-sleep
        print(". ")
        count++
    }
    // Output: . . 
}
```

## 4. Multiplatform Path (KMP / Common)
Condition-based loops in shared code.

```kotlin
fun main() {
    val list = mutableListOf(1, 2)
    while (list.isNotEmpty()) {
        print("${list.removeAt(0)} ")
    }
    // Output: 1 2 
}
```

## 5. Explicit Path (Strictly Typed)
Manual control flow with explicit breaks.

```kotlin
fun main() {
    var x: Int = 0
    while (true) {
        if (x >= 3) break
        x = x + 1
    }
    println(x) // Output: 3
}
```

# The Logic Bridge
// Logic: `while` loops are compiled into `if` + `goto` jump instructions. In Kotlin, the variable declared inside a `do-while` body is visible in the loop condition, a feature that distinguishes it from Java and many other languages, simplifying condition checks that depend on body logic.
