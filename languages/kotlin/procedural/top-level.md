# Top-Level Execution (PRO)

Definition: Kotlin allows functions and properties to exist outside of any class. These are "Top-Level" elements.

## 1. JVM-Legacy (Java-Interop Style)
Calling Kotlin top-level functions from Java.

```kotlin
// In File: MathUtils.kt
fun square(x: Int) = x * x

// Java Call: MathUtilsKt.square(5)
```

## 2. Modern Kotlin (K2 / Idiomatic)
Direct usage in script-like projects.

```kotlin
val VERSION = "2.0"
fun start() = println("System $VERSION")

fun main() { start() } // Output: System 2.0
```

## 3. Kotlin Native (System / C-Interop)
Exporting top-level symbols to C.

```kotlin
// @CName("native_start")
fun nativeStart() { }
```

## 4. Multiplatform Path (KMP / Common)
Shared top-level logic.

```kotlin
fun commonLog(msg: String) = println(msg)
```

## 5. Explicit Path (Strictly Typed)
Explicit visibility and return types.

```kotlin
public val GLOBAL_ID: Int = 100
public fun initSystem(): Unit { }
```

# The Logic Bridge
// Logic: At the bytecode level, the Kotlin compiler generates a wrapper class (e.g., `FilenameKt`) and marks top-level functions as `static` methods. In Kotlin/Native, they are compiled into global symbols in the object file, similar to C functions.
