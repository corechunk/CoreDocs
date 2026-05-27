# Unsigned (CORE)

Definition: Unsigned integers are types that represent only non-negative numbers, effectively doubling the positive range of the corresponding signed type.

## 1. JVM-Legacy (Java-Interop Style)
Handling unsigned via Java 8+ utility methods (Kotlin provides native support now).

```kotlin
val u: UInt = 10u
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using the `u` suffix.

```kotlin
val u = 42u
val ul = 42uL
```

## 3. Kotlin Native (System / C-Interop)
Direct mapping to C unsigned types.

```kotlin
import kotlinx.cinterop.*
val cUInt: uint32_t = 10u
```

## 4. Multiplatform Path (KMP / Common)
Unsigned types are available in `commonMain`.

```kotlin
val id: UInt = 1u
```

## 5. Explicit Path (Strictly Typed)
Explicit unsigned types.

```kotlin
val ub: UByte = 255u
val us: UShort = 65535u
val ui: UInt = 100u
val ul: ULong = 1000uL
```

# The Logic Bridge
// Logic: Unsigned types are implemented as `inline classes` (value classes) in Kotlin, meaning they provide type safety at compile time but are represented as their signed counterparts in JVM bytecode to maintain performance and compatibility.
