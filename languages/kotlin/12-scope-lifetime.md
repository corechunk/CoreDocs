# 12 - Scope & Lifetime (CORE)

Definition: Visibility and memory duration of variables.

## 1. JVM-Legacy (Java-Interop Style)
JVM-style visibility (`private`, `public`).

```kotlin
class Test {
    private val x = 1
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
`internal` visibility and block scoping.

```kotlin
internal val mod = 0
fun main() {
    run { val local = 1 }
}
```

## 3. Kotlin Native (System / C-Interop)
Lifetime management in `memScoped` blocks.

```kotlin
import kotlinx.cinterop.*

fun main() {
    memScoped {
        val ptr = alloc<IntVar>()
        // ptr is valid only in this scope
    }
}
```

## 4. Multiplatform Path (KMP / Common)
Target-agnostic visibility rules.

```kotlin
private fun hide() { }
```

## 5. Explicit Path (Strictly Typed)
Explicit shadowing and types.

```kotlin
val x: Int = 1
fun main() {
    val x: Int = 2 // Shadowing
}
```

# The Logic Bridge
// Logic: Scoping is enforced by the compiler. In Kotlin/Native, `memScoped` provides a way to manage C-memory lifecycle deterministically, similar to an arena allocator, while JVM memory is managed by the Garbage Collector.
