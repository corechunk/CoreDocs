# 23 - Iteration: Definite (CORE)

Definition: Definite iteration in Kotlin is primarily handled by the `for` loop, which works with ranges, arrays, and any object that provides an `iterator()`.

## 1. JVM-Legacy (Java-Interop Style)
Traditional range-based loop.

```kotlin
fun main() {
    // Java-style: for(int i=0; i<3; i++)
    for (i in 0 until 3) {
        print("$i ") // Output: 0 1 2 
    }
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Iterating directly over collections and using progression steps.

```kotlin
fun main() {
    val tech = listOf("K2", "Native", "KMP")
    for (name in tech) {
        print("$name ") // Output: K2 Native KMP 
    }
    
    for (i in 6 downTo 0 step 2) {
        print("$i ") // Output: 6 4 2 0 
    }
}
```

## 3. Kotlin Native (System / C-Interop)
Iterating through a fixed-size C-style array or pointer sequence.

```kotlin
import platform.posix.*

fun main() {
    val buffer = "Kotlin".toCharArray()
    for (i in 0 until buffer.size) {
        putchar(buffer[i].code)
    }
    // Output: Kotlin
}
```

## 4. Multiplatform Path (KMP / Common)
Iteration logic that works across all targets.

```kotlin
fun main() {
    val range = 1..3
    range.forEach { print("$it ") } // Output: 1 2 3 
}
```

## 5. Explicit Path (Strictly Typed)
Using `.withIndex()` to get typed index and value.

```kotlin
fun main() {
    val list: List<String> = listOf("A", "B")
    for ((idx: Int, value: String) in list.withIndex()) {
        println("$idx: $value")
    }
    /* Output:
       0: A
       1: B
    */
}
```

# The Logic Bridge
// Logic: For ranges like `1..10`, the Kotlin compiler is smart enough to optimize the `for` loop into a primitive index-based loop in the bytecode, avoiding the overhead of an `Iterator` object. This makes Kotlin's `for` as fast as Java's manual `for(int i...)` loops.
