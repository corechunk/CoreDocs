# 13 - Storage Classes (SYSTEMS)

Definition: Storage classes define the allocation, initialization, and lifetime of variables. Kotlin provides `lateinit` for late initialization and `by lazy` for lazy initialization.

## 1. JVM-Legacy (Java-Interop Style)
Standard mutable field with null-check initialization.

```kotlin
class Legacy {
    private var data: String? = null
    
    fun get(): String {
        if (data == null) data = "Init"
        return data!!
    }
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using `by lazy` for thread-safe lazy initialization.

```kotlin
val data: String by lazy {
    println("Computing...")
    "Result"
}

fun main() {
    println(data) // Output: Computing... Result
    println(data) // Output: Result
}
```

## 3. Kotlin Native (System / C-Interop)
Lateinit and object pinning in Native.

```kotlin
class Native {
    lateinit var session: String
}

fun main() {
    val n = Native()
    n.session = "Active"
    println(n.session) // Output: Active
}
```

## 4. Multiplatform Path (KMP / Common)
Lazy and lateinit work across all targets.

```kotlin
val commonLazy: Int by lazy { 42 }
```

## 5. Explicit Path (Strictly Typed)
Explicitly defining initialization state.

```kotlin
class Strict {
    var initialized: Boolean = false
    var value: Int = 0
}
```

# The Logic Bridge
// Logic: `lateinit` is only for `var` and non-primitive types; it avoids null-checks by promising the compiler the variable will be set before use. `by lazy` is for `val` and implements the **Delegate Pattern**, creating a hidden `Lazy` object that synchronizes access to ensure the initializer runs only once.
