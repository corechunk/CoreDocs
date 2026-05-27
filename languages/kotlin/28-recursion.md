# 28 - Recursion (CORE)

Definition: Recursion occurs when a function calls itself. Kotlin provides the `tailrec` modifier to optimize tail-recursive functions into loops to prevent stack overflow.

## 1. JVM-Legacy (Java-Interop Style)
Standard recursive function (vulnerable to StackOverflow).

```kotlin
fun factorial(n: Int): Int {
    if (n <= 1) return 1
    return n * factorial(n - 1)
}

fun main() {
    println(factorial(5)) // Output: 120
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using `tailrec` for memory-safe recursion.

```kotlin
tailrec fun findFixpoint(x: Double = 1.0): Double {
    val next = Math.cos(x)
    if (Math.abs(x - next) < 1E-10) return next
    return findFixpoint(next)
}

fun main() {
    println(findFixpoint()) // Output: 0.7390851332...
}
```

## 3. Kotlin Native (System / C-Interop)
Recursion in native code with fixed stack sizes.

```kotlin
fun nativeCount(n: Int) {
    if (n < 0) return
    print("$n ")
    nativeCount(n - 1)
}

fun main() {
    nativeCount(3) // Output: 3 2 1 0 
}
```

## 4. Multiplatform Path (KMP / Common)
Recursive logic shared across platforms.

```kotlin
fun fibonacci(n: Int): Int = if (n <= 1) n else fibonacci(n - 1) + fibonacci(n - 2)

fun main() {
    println(fibonacci(6)) // Output: 8
}
```

## 5. Explicit Path (Strictly Typed)
Tail-recursive factorial with explicit accumulator.

```kotlin
tailrec fun fact(n: Int, acc: Int = 1): Int {
    if (n <= 1) return acc
    return fact(n - 1, n * acc)
}

fun main() {
    val result: Int = fact(5)
    println(result) // Output: 120
}
```

# The Logic Bridge
// Logic: The `tailrec` modifier tells the compiler to check if the recursive call is the last action in the function. If it is, the compiler rewrites the recursion as a high-performance `while` loop in the bytecode (JVM) or machine code (Native), eliminating the risk of a `StackOverflowError`.
