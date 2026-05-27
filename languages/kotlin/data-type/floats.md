# Floats (CORE)

Definition: Floating-point types for decimal numbers. `Double` is the default (64-bit), while `Float` is 32-bit.

## 1. JVM-Legacy (Java-Interop Style)
Standard `Double` and `Float`.

```kotlin
val d: Double = 3.14
val f: Float = 3.14f
```

## 2. Modern Kotlin (K2 / Idiomatic)
Inferred `Double`.

```kotlin
val pi = 3.14
```

## 3. Kotlin Native (System / C-Interop)
C-compatible float types.

```kotlin
import kotlinx.cinterop.*
val cFloat: float_t = 3.14f
```

## 4. Multiplatform Path (KMP / Common)
Portable floats.

```kotlin
val price: Double = 19.99
```

## 5. Explicit Path (Strictly Typed)
Explicit float types.

```kotlin
val f: Float = 1.0f
val d: Double = 1.0
```

# The Logic Bridge
// Logic: `Float` requires the `f` or `F` suffix. Kotlin follows IEEE 754 standards for floating-point arithmetic on all platforms.
