# Integers (CORE)

Definition: Kotlin provides several integer types with different sizes and ranges. `Int` is the default 32-bit integer.

## 1. JVM-Legacy (Java-Interop Style)
Using `Int` and `Long` which map to `int` and `long`.

```kotlin
val i: Int = 10
val l: Long = 100L
```

## 2. Modern Kotlin (K2 / Idiomatic)
Type inference for integers.

```kotlin
val i = 42
val l = 42L
```

## 3. Kotlin Native (System / C-Interop)
C-compatible integer types.

```kotlin
import kotlinx.cinterop.*
val cInt: int32_t = 10
```

## 4. Multiplatform Path (KMP / Common)
Portable integer types.

```kotlin
val count: Int = 0
```

## 5. Explicit Path (Strictly Typed)
Explicit width declarations.

```kotlin
val b: Byte = 1
val s: Short = 10
val i: Int = 100
val l: Long = 1000L
```

# The Logic Bridge
// Logic: Kotlin integers are optimized to JVM primitives. `Long` requires an `L` suffix. In Kotlin/Native, these map to the target architecture's native integer widths.
