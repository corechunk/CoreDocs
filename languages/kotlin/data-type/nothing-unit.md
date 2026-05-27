# Nothing & Unit (CORE)

Definition: `Unit` is the equivalent of `void` but is a real object. `Nothing` is a type that has no values and represents a computation that never finishes.

## 1. JVM-Legacy (Java-Interop Style)
Functions returning nothing (Unit).

```kotlin
fun log(): Unit { println("Log") }
```

## 2. Modern Kotlin (K2 / Idiomatic)
Implicit `Unit`.

```kotlin
fun log() { println("Log") }
```

## 3. Kotlin Native (System / C-Interop)
`Nothing` used in exit functions.

```kotlin
import platform.posix.*
// exit(1) // Returns Nothing
```

## 4. Multiplatform Path (KMP / Common)
Shared `Unit`/`Nothing`.

```kotlin
fun fail(): Nothing = throw Exception()
```

## 5. Explicit Path (Strictly Typed)
Explicit declarations.

```kotlin
val u: Unit = Unit
```

# The Logic Bridge
// Logic: `Unit` is a singleton. `Nothing` is a subtype of all types, allowing it to be used where any value is expected (like a `return` in a `when` branch).
