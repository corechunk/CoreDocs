# 31 - Sequential Collections (CORE - Hub)

Definition: Sequential collections store elements in a specific order. Kotlin distinguishes between Immutable (read-only) and Mutable collections, which is a key design choice for safety.

## Collection Categories

| Category | Types | Hub Link |
| :--- | :--- | :--- |
| **Fixed Array** | `Array<T>` | [fixed.md](./array/fixed.md) |
| **Immutable List** | `List<T>` | [lists.md](./array/lists.md) |
| **Mutable List** | `MutableList<T>` | [lists.md](./array/lists.md) |
| **Set** | `Set<T>` | [32-associative-collections.md](./32-associative-collections.md) |

## 1. JVM-Legacy (Java-Interop Style)
Using `java.util.ArrayList` explicitly.

```kotlin
import java.util.ArrayList

fun main() {
    val list = ArrayList<String>()
    list.add("Java")
    println(list) // Output: [Java]
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using the `listOf()` and `mutableListOf()` factory functions.

```kotlin
fun main() {
    val readOnly = listOf("Kotlin", "K2")
    val mutable = mutableListOf(1, 2)
    
    mutable.add(3)
    println(readOnly) // Output: [Kotlin, K2]
    println(mutable)  // Output: [1, 2, 3]
}
```

## 3. Kotlin Native (System / C-Interop)
Using native arrays or C-pointers for sequences.

```kotlin
import kotlinx.cinterop.*

fun main() {
    val nativeArray = intArrayOf(10, 20, 30)
    println(nativeArray.size) // Output: 3
}
```

## 4. Multiplatform Path (KMP / Common)
KMP-compatible collection interfaces.

```kotlin
fun main() {
    val commonList: List<Int> = listOf(42)
    println(commonList.first()) // Output: 42
}
```

## 5. Explicit Path (Strictly Typed)
Explicitly declaring the collection type and mutability.

```kotlin
fun main() {
    val names: List<String> = listOf<String>("Core", "Chunk")
    val scores: MutableList<Int> = mutableListOf<Int>(100)
    
    scores.add(50)
    println(names)  // Output: [Core, Chunk]
    println(scores) // Output: [100, 50]
}
```

# The Logic Bridge
// Logic: Kotlin's `List` is a read-only interface, while `MutableList` extends it to add modification methods. At the JVM level, both often compile down to the same `java.util.ArrayList`, but the Kotlin compiler enforces the "read-only" contract at compile time, preventing accidental modifications.
