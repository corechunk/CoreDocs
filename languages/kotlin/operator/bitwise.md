# Bitwise Operators (CORE)

Definition: Operators for manipulating individual bits. In Kotlin, these are named functions used as infix operators.

## 1. JVM-Legacy (Java-Interop Style)
Using `shl`, `shr`, `and`, `or`, `xor`, `inv`.

```kotlin
val bits = 0b0001 shl 2
```

## 2. Modern Kotlin (K2 / Idiomatic)
Clean bitwise syntax.

```kotlin
val mask = 0xF0 and 0x0F
```

## 3. Kotlin Native (System / C-Interop)
Mapping directly to CPU bitwise instructions.

```kotlin
val b = 1.shl(2)
```

## 4. Multiplatform Path (KMP / Common)
Portable bitwise logic.

```kotlin
val x = 1 or 2
```

## 5. Explicit Path (Strictly Typed)
Explicit types for bitwise operations.

```kotlin
val res: Int = 1.inv()
```

# The Logic Bridge
// Logic: Kotlin uses named functions like `shl` (shift left) instead of `<<` to avoid ambiguity and maintain a clean grammar.
