# Booleans (CORE)

Definition: Represents `true` or `false`.

## 1. JVM-Legacy (Java-Interop Style)
Standard `Boolean`.

```kotlin
val b: Boolean = true
```

## 2. Modern Kotlin (K2 / Idiomatic)
Inferred `Boolean`.

```kotlin
val isOk = true
```

## 3. Kotlin Native (System / C-Interop)
Mapping to C `bool`.

```kotlin
import kotlinx.cinterop.*
```

## 4. Multiplatform Path (KMP / Common)
Portable `Boolean`.

```kotlin
val flag: Boolean = false
```

## 5. Explicit Path (Strictly Typed)
Explicit logic.

```kotlin
val result: Boolean = 10 > 5
```

# The Logic Bridge
// Logic: Booleans are strict in Kotlin. No truthiness for other types.
