# 33 - Structs Base (CORE - Hub)

Definition: Kotlin uses the `data class` as the gateway to Procedural-style data modeling. It acts like a "Plain Old Data" container, grouping related variables into a single record.

## Deep-Dive Reference
For modular procedural architecture:
- [Procedural Mechanisms](./procedural/00-start.md)

---

## 1. JVM-Legacy (Java-Interop Style)
Traditional property-based grouping.

```kotlin
class Config(var host: String, var port: Int)

fun main() {
    val c = Config("localhost", 80)
    c.port = 8080 // Access via dot-operator
    println("${c.host}:${c.port}") // Output: localhost:8080
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Automated data record generation.

```kotlin
data class Config(val host: String, val port: Int)

fun main() {
    val c = Config("127.0.0.1", 443)
    println(c) // Output: Config(host=127.0.0.1, port=443)
}
```

## 3. Kotlin Native (System / C-Interop)
Interacting with C-structs via `CStructVar`.

```kotlin
import kotlinx.cinterop.*
// memScoped { val s = alloc<stat>() }
```

## 4. Multiplatform Path (KMP / Common)
Shared data models.

```kotlin
data class User(val id: Long, val name: String)
```

## 5. Explicit Path (Strictly Typed)
Explicit constructor and property types.

```kotlin
data class Record constructor(
    val id: Int,
    val data: String
)
```

# The Logic Bridge
// Logic: `data class` provides a zero-boilerplate way to group data. Under the hood, the compiler generates `componentN()` functions, allowing for procedural patterns like **Destructuring Declarations** (`val (h, p) = config`).
