# 29 - Passing Mechanisms (CORE)

Definition: Kotlin passes all arguments by value. However, for object references, the value being passed is the address of the object, meaning you can modify the object's internal state but not the reference itself.

## 1. JVM-Legacy (Java-Interop Style)
Standard reference-passing behavior.

```kotlin
class Box(var value: Int)

fun update(box: Box) {
    box.value = 100 // Modifies object content
}

fun main() {
    val b = Box(0)
    update(b)
    println(b.value) // Output: 100
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Passing primitive-like types (Int, String) which are immutable.

```kotlin
fun increment(x: Int) {
    // x = x + 1 // Error: Val cannot be reassigned
}

fun main() {
    val a = 5
    increment(a)
    println(a) // Output: 5
}
```

## 3. Kotlin Native (System / C-Interop)
Passing pointers and references to C-memory.

```kotlin
import kotlinx.cinterop.*
import platform.posix.*

fun nativePass(ptr: CPointer<ByteVar>) {
    // Interacting with raw memory
    println(ptr.pointed)
}

fun main() {
    // Native pointer logic
}
```

## 4. Multiplatform Path (KMP / Common)
Consistent passing logic across all targets.

```kotlin
fun modifyList(list: MutableList<Int>) {
    list.add(1)
}

fun main() {
    val l = mutableListOf<Int>()
    modifyList(l)
    println(l.size) // Output: 1
}
```

## 5. Explicit Path (Strictly Typed)
Explicitly showing that parameters are immutable `val` references.

```kotlin
fun process(valParam: String): Unit {
    // valParam = "New" // Compiler Error
    println(valParam)
}

fun main() {
    process("Strict") // Output: Strict
}
```

# The Logic Bridge
// Logic: In Kotlin, all function parameters are implicitly `val`, meaning they cannot be reassigned within the function body. For JVM primitives (`Int`, `Double`), the actual value is copied. For objects, the reference (memory address) is copied. Kotlin/Native's C-interop extends this by allowing explicit pointer passing (`CPointer`), which requires manual memory management via `memScoped` blocks.
