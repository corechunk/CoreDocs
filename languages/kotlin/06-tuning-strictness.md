# 06 - Tuning & Strictness (PRO)

Definition: Tuning and strictness involve configuring the compiler to enforce specific rules or optimize for performance. In Kotlin, this includes opt-in requirements and compiler flags.

## 1. JVM-Legacy (Java-Interop Style)
Standard compiler strictness.

```kotlin
fun main() {
    println("Standard Strictness")
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using `@OptIn` for experimental or unstable features.

```kotlin
@OptIn(kotlin.RequiresOptIn::class)
fun experimentalFeature() {
    println("Experimental")
}

fun main() {
    experimentalFeature() // Output: Experimental
}
```

## 3. Kotlin Native (System / C-Interop)
Enforcing strict memory rules in Native.

```kotlin
import kotlinx.cinterop.*

fun main() {
    // Native strictness often involves pointer safety
}
```

## 4. Multiplatform Path (KMP / Common)
Shared strictness configurations.

```kotlin
@RequiresOptIn(level = RequiresOptIn.Level.ERROR)
annotation class InternalApi

@InternalApi
fun hidden() { }
```

## 5. Explicit Path (Strictly Typed)
Explicitly enabling compiler warnings as errors.

```kotlin
// In build.gradle.kts:
// allWarningsAsErrors = true
```

# The Logic Bridge
// Logic: Kotlin uses the `@RequiresOptIn` mechanism to manage API stability. This allows developers to use experimental features while being explicitly aware of the risks. At the compiler level, flags like `-Werror` can be used to treat all warnings as compilation errors, ensuring higher code quality.
