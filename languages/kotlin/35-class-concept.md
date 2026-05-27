# 35 - Class Concept (CORE - Hub)

Definition: The `class` is the gateway to Object-Oriented Programming. It encapsulates **State** (Properties) and **Behavior** (Methods) into a cohesive unit.

## Deep-Dive Reference
For complex hierarchies and pillars:
- [Advanced OOP](./oop/00-start.md)

---

## 1. JVM-Legacy (Java-Interop Style)
Explicit member and accessor logic.

```kotlin
class Counter {
    private var value = 0
    fun increment() { value++ }
    fun get() = value
}

fun main() {
    val c = Counter()
    c.increment()
    println(c.get()) // Output: 1
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Concise class with primary constructor.

```kotlin
class Counter(var value: Int = 0) {
    fun increment() { value++ }
}

fun main() {
    val c = Counter()
    c.increment()
    println(c.value) // Output: 1
}
```

## 3. Kotlin Native (System / C-Interop)
Classes with `init` blocks for native setup.

```kotlin
class NativeApp {
    init { println("Native Init") }
}
```

## 4. Multiplatform Path (KMP / Common)
Abstract shared behavior.

```kotlin
open class PlatformService {
    open fun run() { }
}
```

## 5. Explicit Path (Strictly Typed)
Explicitly defined visibility and accessors.

```kotlin
class Account constructor(initial: Double) {
    var balance: Double = initial
        private set
}
```

# The Logic Bridge
// Logic: In Kotlin, properties are more than just fields; they are a combination of a private field and public accessors. This ensures that even simple data access follows OOP encapsulation principles by default.
