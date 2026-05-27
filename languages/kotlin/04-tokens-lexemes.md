# 04 - Tokens & Lexemes (CORE)

Definition: Tokens are the atomic units of Kotlin source code. Lexemes are the actual character sequences representing these tokens.

## 1. JVM-Legacy (Java-Interop Style)
Standard JVM-compatible tokenization.

```kotlin
val count = 10 // Tokens: val, count, =, 10
```

## 2. Modern Kotlin (K2 / Idiomatic)
K2 optimized tokens and smart-cast markers.

```kotlin
val x: Int? = 5
if (x != null) {
    // x is now a smart-cast token
    println(x + 1) // Output: 6
}
```

## 3. Kotlin Native (System / C-Interop)
C-interop specific tokens (e.g., `CPointer`, `memScoped`).

```kotlin
import kotlinx.cinterop.*

fun main() {
    // native token logic
}
```

## 4. Multiplatform Path (KMP / Common)
Tokens recognized across all platforms.

```kotlin
fun main() {
    val s = "Lexeme"
    println(s) // Output: Lexeme
}
```

## 5. Explicit Path (Strictly Typed)
Explicitly identifying token boundaries.

```kotlin
val result: Int = 10.plus(5)
```

# The Logic Bridge
// Logic: The Lexer breaks source text into tokens. In Kotlin 2.0, the lexer is part of a high-performance frontend that produces a PSI (Program Structure Interface) tree, which is later used for type checking and code generation across JVM and Native backends.
