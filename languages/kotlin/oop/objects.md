# Objects & Companions (PRO)

Definition: Singletons and static-like members in Kotlin.

## 1. JVM-Legacy (Java-Interop Style)
Using `companion object` to simulate Java's `static`.

```kotlin
class App {
    companion object {
        const val VERSION = "1.0"
        @JvmStatic fun start() { }
    }
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using `object` for thread-safe singletons.

```kotlin
object Database {
    val name = "Core"
}
```

## 3. Kotlin Native (System / C-Interop)
Objects in Native and thread-safety implications.

```kotlin
object NativeConfig {
    // Shared between threads (immutable)
}
```

## 4. Multiplatform Path (KMP / Common)
Shared singletons.

```kotlin
expect object PlatformEnv
```

## 5. Explicit Path (Strictly Typed)
Explicit object types.

```kotlin
val db: Database = Database
```

# The Logic Bridge
// Logic: An `object` in Kotlin is a lazy-initialized singleton. Under the hood, the compiler generates a class with a private constructor and a static `INSTANCE` field, ensuring the instance is created only once.
