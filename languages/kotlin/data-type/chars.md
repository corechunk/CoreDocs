# Characters (CORE)

Definition: Represents a single 16-bit Unicode character.

## 1. JVM-Legacy (Java-Interop Style)
Standard `Char`.

```kotlin
val c: Char = 'A'
```

## 2. Modern Kotlin (K2 / Idiomatic)
Inferred `Char`.

```kotlin
val c = 'K'
```

## 3. Kotlin Native (System / C-Interop)
Mapping to C `char` (8-bit) vs Kotlin `Char` (16-bit).

```kotlin
import kotlinx.cinterop.*
// C char is usually Byte in Kotlin
```

## 4. Multiplatform Path (KMP / Common)
Portable `Char`.

```kotlin
val x: Char = '!'
```

## 5. Explicit Path (Strictly Typed)
Explicit Unicode.

```kotlin
val c: Char = '\u0041' // 'A'
```

# The Logic Bridge
// Logic: `Char` literals are enclosed in single quotes. Unlike Java, Kotlin does not implicitly treat `Char` as an integer; you must use `.code` to get its numeric value.
