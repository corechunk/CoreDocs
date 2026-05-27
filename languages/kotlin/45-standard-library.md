# Standard Library (PRO)

Definition: The core set of utilities provided with the language.

## 1. JVM-Legacy (Java-Interop Style)
`kotlin.jvm.*`.

```kotlin
import kotlin.jvm.JvmStatic
```

## 2. Modern Kotlin (K2 / Idiomatic)
Scope functions: `let`, `run`, `with`, `apply`, `also`.

```kotlin
val res = "A".let { it.length }
```

## 3. Kotlin Native (System / C-Interop)
`kotlin.native.*` and `platform.*`.

```kotlin
import platform.linux.*
```

## 4. Multiplatform Path (KMP / Common)
`kotlin.*` (The core common lib).

```kotlin
import kotlin.math.*
```

## 5. Explicit Path (Strictly Typed)
Explicitly calling standard functions.

```kotlin
val x: Int = kotlin.math.abs(-10)
```

# The Logic Bridge
// Logic: The standard library is thin, adding idiomatic power to platform-specific APIs. It's the "glue" that makes Kotlin feel consistent across all targets.
