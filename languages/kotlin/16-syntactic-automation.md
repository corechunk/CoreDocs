# 16 - Syntactic Automation (SYSTEMS)

Definition: Syntactic automation refers to features where the compiler generates code for you, such as Data Classes, Inline Classes, and Delegated Properties.

## 1. JVM-Legacy (Java-Interop Style)
Manually writing getters/setters and equals/hashCode.

```kotlin
class Legacy(val id: Int) {
    override fun equals(other: Any?) = (other as? Legacy)?.id == id
    override fun hashCode() = id
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using `data class` to automate boilerplate.

```kotlin
data class Modern(val id: Int)

fun main() {
    val m = Modern(1)
    println(m) // Output: Modern(id=1)
}
```

## 3. Kotlin Native (System / C-Interop)
Using `value class` (Inline class) for zero-cost wrappers.

```kotlin
@JvmInline
value class NativeId(val id: Int)

fun main() {
    val n = NativeId(10)
    println(n.id) // Output: 10
}
```

## 4. Multiplatform Path (KMP / Common)
Property delegation (`by`).

```kotlin
var observed: String by Delegates.observable("Init") { _, old, new ->
    println("$old -> $new")
}

fun main() {
    observed = "Update" // Output: Init -> Update
}
```

## 5. Explicit Path (Strictly Typed)
Explicitly implementing a delegate.

```kotlin
class MyDelegate {
    operator fun getValue(thisRef: Any?, property: KProperty<*>) = "Value"
}
```

# The Logic Bridge
// Logic: Syntactic automation like `data class` or `value class` shifts the burden of writing repetitive code to the compiler. `value class` is particularly powerful as it inlines the underlying value at the call site, providing the type safety of a class with the performance of a primitive.
