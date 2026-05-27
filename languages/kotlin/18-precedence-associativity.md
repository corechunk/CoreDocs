# 18 - Precedence & Associativity (CORE)

Definition: Precedence determines the order in which operators are evaluated in an expression. Associativity determines the order when operators have the same precedence.

## 1. JVM-Legacy (Java-Interop Style)
Standard mathematical order of operations (PEMDAS).

```kotlin
fun main() {
    // Java equivalent: 10 + 20 * 2 = 50
    val result = 10 + 20 * 2
    println(result) // Output: 50
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using parentheses for clarity, which is the idiomatic preference in Kotlin.

```kotlin
fun main() {
    val result = 10 + (20 * 2)
    println(result) // Output: 50
}
```

## 3. Multiplatform Path (KMP / Common)
Evaluation rules are consistent across all platforms.

```kotlin
fun main() {
    val logic = true || false && false // && has higher precedence than ||
    println(logic) // Output: true
}
```

## 4. Explicit Path (Strictly Typed)
Explicitly nested expressions to show exact evaluation order.

```kotlin
fun main() {
    val x: Int = 10
    val y: Int = 5
    val z: Int = 2
    
    val res: Int = x.plus(y.times(z))
    println(res) // Output: 20
}
```

# The Logic Bridge
// Logic: Kotlin follows standard C/Java precedence rules. Multiplicative operators (`*`, `/`, `%`) are evaluated before additive operators (`+`, `-`). Among logical operators, `!` has the highest precedence, followed by `&&`, and then `||`.
