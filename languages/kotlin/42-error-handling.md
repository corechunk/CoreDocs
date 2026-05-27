# 42 - Error Handling (CORE)

Definition: Kotlin handles errors primarily through Exceptions. Unlike Java, all exceptions in Kotlin are "Unchecked," meaning you are not forced to wrap code in `try-catch` blocks. Kotlin also promotes the use of `Result` types for functional error handling.

## 1. JVM-Legacy (Java-Interop Style)
Traditional `try-catch-finally` blocks.

```kotlin
fun main() {
    try {
        val res = 10 / 0
    } catch (e: ArithmeticException) {
        println("Error: ${e.message}") // Output: Error: / by zero
    } finally {
        println("Clean up") // Output: Clean up
    }
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using `try` as an expression and the `Result` type.

```kotlin
fun main() {
    val result: Result<Int> = runCatching { 10 / 2 }
    
    result.onSuccess { println(it) } // Output: 5
          .onFailure { println("Failed") }
}
```

## 3. Kotlin Native (System / C-Interop)
Handling POSIX error codes via `errno`.

```kotlin
import platform.posix.*

fun main() {
    val fd = open("non_existent", O_RDONLY)
    if (fd == -1) {
        println("Native Error: $errno") // Output: Native Error: 2
    }
}
```

## 4. Multiplatform Path (KMP / Common)
Shared exception logic and custom Error types.

```kotlin
class KmpException(msg: String) : Exception(msg)

fun main() {
    // throw KmpException("Common Failure")
    println("KMP Error Ready") // Output: KMP Error Ready
}
```

## 5. Explicit Path (Strictly Typed)
Explicitly declaring the return type as `Any` or a sealed result class.

```kotlin
sealed class Response {
    data class Success(val data: String) : Response()
    data class Error(val code: Int) : Response()
}

fun fetch(): Response = Response.Success("Data")

fun main() {
    val res: Response = fetch()
    println(res) // Output: Success(data=Data)
}
```

# The Logic Bridge
// Logic: Kotlin's decision to have only Unchecked Exceptions simplifies API design and reduces verbosity. At the JVM level, this means the compiler doesn't add `throws` clauses to method signatures unless explicitly requested via the `@Throws` annotation (which is required for Java-interop). `runCatching` is an idiomatic wrapper that captures any `Throwable` and encapsulates it into a `Result` object for functional processing.
