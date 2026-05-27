# 17 - Operators (CORE - Hub)

Definition: Operators in Kotlin are symbols that perform operations on operands. Most operators are "syntactic sugar" for specific function calls, allowing for operator overloading.

## 1. JVM-Legacy (Java-Interop Style)
Standard Java-style operator usage.

```kotlin
fun main() {
    val a = 10
    val b = 5
    // Java-style: a + b, a == b
    println("Sum: ${a + b}")   // Output: Sum: 15
    println("Equals: ${a == b}") // Output: Equals: false
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using range and containment operators.

```kotlin
fun main() {
    val x = 5
    // 'in' operator for ranges
    if (x in 1..10) {
        println("$x is in range") // Output: 5 is in range
    }
}
```

## 3. Kotlin Native (System / C-Interop)
Using bitwise operators and pointer-like logic (via `shl`, `shr`).

```kotlin
fun main() {
    val bits = 0b0001
    // Native bit-shifting
    val shifted = bits shl 2 
    println("Shifted: $shifted") // Output: Shifted: 4
}
```

## 4. Multiplatform Path (KMP / Common)
Core operators that work identically on all platforms.

```kotlin
fun main() {
    val res = (10 * 2) / 5
    println(res) // Output: 4
}
```

## 5. Explicit Path (Strictly Typed)
Calling the underlying operator functions explicitly.

```kotlin
fun main() {
    val a: Int = 10
    val b: Int = 2
    
    // Explicit function calls
    val sum: Int = a.plus(b)
    val check: Boolean = a.equals(b)
    
    println(sum)   // Output: 12
    println(check) // Output: false
}
```

# The Logic Bridge
// Logic: Kotlin uses "Operator Overloading" by convention. The expression `a + b` is compiled to `a.plus(b)`. This applies to comparison (`compareTo`), indexing (`get`/`set`), and even function calls (`invoke`). In Kotlin/Native, bitwise operators like `shl` are mapped directly to CPU instructions for maximum performance.
