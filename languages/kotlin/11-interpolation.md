# 11 - Interpolation (CORE)

Definition: Embedding expressions in strings using `$` or `${}`.

## 1. JVM-Legacy (Java-Interop Style)
String concatenation using `+`.

```kotlin
val s = "Hello " + "World"
```

## 2. Modern Kotlin (K2 / Idiomatic)
Idiomatic `$` interpolation.

```kotlin
val name = "Core"
println("Hi $name") // Output: Hi Core
```

## 3. Kotlin Native (System / C-Interop)
Interpolation in strings used with native IO.

```kotlin
import platform.posix.*

fun main() {
    val x = 10
    printf("Value: %d\n", x) // POSIX way
}
```

## 4. Multiplatform Path (KMP / Common)
Common interpolation logic.

```kotlin
val v = 2.0
val msg = "V: $v"
```

## 5. Explicit Path (Strictly Typed)
Explicit expression interpolation.

```kotlin
val res: String = "Sum: ${10 + 20}"
```

# The Logic Bridge
// Logic: The compiler converts interpolation into `StringBuilder` calls or `makeConcatWithConstants` for efficiency. In Kotlin/Native, it's optimized to avoid excessive allocations during string construction.
