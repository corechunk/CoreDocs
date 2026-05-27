# Math Operators (CORE)

Definition: Standard arithmetic operators.

## 1. JVM-Legacy (Java-Interop Style)
Standard `+`, `-`, `*`, `/`, `%`.

```kotlin
val x = 10 + 5
```

## 2. Modern Kotlin (K2 / Idiomatic)
Infix usage and operator functions.

```kotlin
val x = 10.plus(5)
```

## 3. Kotlin Native (System / C-Interop)
Native math operations.

```kotlin
val x = 10 shl 1
```

## 4. Multiplatform Path (KMP / Common)
Common arithmetic.

```kotlin
val avg = 10 / 2
```

## 5. Explicit Path (Strictly Typed)
Explicitly typed math.

```kotlin
val sum: Int = 10 + 20
```

# The Logic Bridge
// Logic: Arithmetic operators map to named functions in the class, which the compiler optimizes to primitive instructions on the JVM and Native.
