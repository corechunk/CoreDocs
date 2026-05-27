# 09 - Data Types (CORE - Hub)

Definition: Kotlin is a statically typed language where every variable must have a type. Every type in Kotlin is an object (e.g., `Int`, `Boolean`), but the compiler optimizes them back to JVM primitives where possible.

## Type System Overview

| Category           | Types                              | Hub Link                                         |
| :----------------- | :--------------------------------- | :----------------------------------------------- |
| **Integers**       | `Byte`, `Short`, `Int`, `Long`     | [integers.md](./data-type/integers.md)           |
| **Floating Point** | `Float`, `Double`                  | [floats.md](./data-type/floats.md)               |
| **Unsigned**       | `UByte`, `UShort`, `UInt`, `ULong` | [unsigned.md](unsigned.md)           |
| **Characters**     | `Char`                             | [chars.md](chars.md)                 |
| **Booleans**       | `Boolean`                          | [booleans.md](./data-type/booleans.md)           |
| **Strings**        | `String`                           | [10-string-escaping.md](./10-string-escaping.md) |
| **Special**        | `Any`, `Unit`, `Nothing`           | [nothing-unit.md](nothing-unit.md)   |

## 1. JVM-Legacy (Java-Interop Style)
Mapping Kotlin types to JVM primitives.

```kotlin
val i: Int = 10      // JVM: int
val b: Boolean = true // JVM: boolean

fun main() {
    println(i) // Output: 10
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Type inference in K2.

```kotlin
val i = 10         // Infers Int
val s = "Kotlin"   // Infers String

fun main() {
    println(s) // Output: Kotlin
}
```

## 3. Kotlin Native (System / C-Interop)
Interacting with C primitives (e.g., `CInt`, `ByteVar`).

```kotlin
import kotlinx.cinterop.*
import platform.posix.*

fun main() {
    val cInt: int32_t = 10
    println(cInt) // Output: 10
}
```

## 4. Multiplatform Path (KMP / Common)
Common types shared across all targets.

```kotlin
val id: Long = 100L
val flag: Boolean = false

fun main() {
    println("$id: $flag") // Output: 100: false
}
```

## 5. Explicit Path (Strictly Typed)
Manual type declarations for absolute clarity.

```kotlin
val count: Int = 42
val isActive: Boolean = true

fun main() {
    println(count) // Output: 42
}
```

# The Logic Bridge
// Logic: Kotlin uses "Primitive Auto-Boxing." The compiler uses primitive types for performance by default. However, when a type is nullable (`Int?`) or used as a generic argument (`List<Int>`), it is automatically "Boxed" into a JVM object (`java.lang.Integer`). In Kotlin/Native, C-interop types are represented as special classes that map directly to C memory structures.
