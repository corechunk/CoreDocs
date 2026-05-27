# 37 - IO Streams (CORE)

Definition: IO Streams handle input and output. In Kotlin, this includes standard console IO (`print`, `readln`) and higher-level stream wrappers for file and network operations.

## 1. JVM-Legacy (Java-Interop Style)
Using `java.util.Scanner` for input.

```kotlin
import java.util.Scanner

fun main() {
    // val sc = Scanner(System.`in`)
    // val input = sc.next()
    println("Java IO Style") // Output: Java IO Style
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using the concise `readln()` and `println()`.

```kotlin
fun main() {
    print("Enter: ")
    // val input = readln() 
    println("Echo: Kotlin") // Output: Echo: Kotlin
}
```

## 3. Kotlin Native (System / C-Interop)
Using POSIX `printf` and `scanf`.

```kotlin
import platform.posix.*

fun main() {
    printf("Native Out\n") // Output: Native Out
}
```

## 4. Multiplatform Path (KMP / Common)
Common IO is limited, but KMP libraries like `okio` or `kotlinx-io` bridge the gap.

```kotlin
fun main() {
    // Standard println works everywhere
    println("Universal Out") // Output: Universal Out
}
```

## 5. Explicit Path (Strictly Typed)
Explicitly using `System.out` or typed stream writers.

```kotlin
fun main() {
    val output: java.io.PrintStream = System.out
    output.println("Explicit IO") // Output: Explicit IO
}
```

# The Logic Bridge
// Logic: `println()` is a top-level function in the Kotlin standard library. On the JVM, it maps to `System.out.println()`. In Kotlin/Native, it maps to a sequence of POSIX calls. `readln()` (introduced in 1.6) is the modern, null-safe replacement for `readLine()!!`, designed to simplify common CLI input tasks.
