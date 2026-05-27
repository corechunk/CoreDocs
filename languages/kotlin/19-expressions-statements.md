# 19 - Expressions & Statements (CORE)

Definition: A statement is a command that performs an action (e.g., variable declaration). An expression is a piece of code that evaluates to a value. In Kotlin, almost everything is an expression (including `if` and `try`).

## 1. JVM-Legacy (Java-Interop Style)
Using `if` as a statement (traditional Java way).

```kotlin
fun main() {
    val a = 10
    val b = 20
    var max = 0
    
    // If as a statement
    if (a > b) {
        max = a
    } else {
        max = b
    }
    println(max) // Output: 20
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using `if` as an expression to assign a value directly.

```kotlin
fun main() {
    val a = 10
    val b = 20
    
    // If as an expression
    val max = if (a > b) a else b
    
    println(max) // Output: 20
}
```

## 3. Multiplatform Path (KMP / Common)
Expressions are core to Kotlin's design and work everywhere.

```kotlin
fun main() {
    val result = try { "42".toInt() } catch (e: Exception) { 0 }
    println(result) // Output: 42
}
```

## 4. Explicit Path (Strictly Typed)
Explicitly defining the return type of expression blocks.

```kotlin
fun main() {
    val status: String = if (true) {
        println("Logic inside")
        "Success" // Last line is the return value
    } else {
        "Failure"
    }
    println(status) // Output: Success
}
```

# The Logic Bridge
// Logic: By making structures like `if`, `when`, and `try` expressions, Kotlin reduces the need for mutable `var` variables and temporary state. At the bytecode level, the compiler generates the same jump instructions as a Java `if` statement but ensures the result is left on the stack for assignment.
