# 26 - Function Basics (CORE)

Definition: Functions are the fundamental building blocks of Kotlin programs. They are declared using the `fun` keyword and can exist at the top level, inside classes, or even inside other functions.

## 1. JVM-Legacy (Java-Interop Style)
Traditional method declaration.

```kotlin
// Java equivalent: public int add(int a, int b) { return a + b; }
fun add(a: Int, b: Int): Int {
    return a + b
}

fun main() {
    println(add(5, 3)) // Output: 8
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Single-expression functions and named/default arguments.

```kotlin
// Concise single-expression
fun greet(name: String = "Guest") = "Hello, $name"

fun main() {
    println(greet())              // Output: Hello, Guest
    println(greet(name = "User")) // Output: Hello, User
}
```

## 3. Kotlin Native (System / C-Interop)
Top-level functions acting as C-entry points or calling POSIX.

```kotlin
import platform.posix.*

fun nativeLog(msg: String) {
    printf("[Native]: %s\n", msg)
}

fun main() {
    nativeLog("Function call") // Output: [Native]: Function call
}
```

## 4. Multiplatform Path (KMP / Common)
Shared function logic in `commonMain`.

```kotlin
fun calculate(x: Int): Int = x * x

fun main() {
    println(calculate(4)) // Output: 16
}
```

## 5. Explicit Path (Strictly Typed)
Explicitly defining all parameters and the `Unit` return type.

```kotlin
fun logInfo(message: String): Unit {
    val prefix: String = "[INFO]: "
    println(prefix + message)
}

fun main(): Unit {
    logInfo("Explicit call") // Output: [INFO]: Explicit call
}
```

# The Logic Bridge
// Logic: Kotlin functions are first-class citizens. At the JVM level, top-level functions are compiled into static methods of a generated class (e.g., `FileKt.class`). In Kotlin/Native, they are compiled into standard C-style symbols. Named and default arguments are handled at the call site by the compiler, which generates the necessary overhead to map arguments correctly.
