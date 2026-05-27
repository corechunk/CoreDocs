# Extension Functions (PRO)

Definition: Extensions allow you to add new functionality to an existing class without inheriting from it.

## 1. JVM-Legacy (Java-Interop Style)
Extensions as static methods with the receiver as the first argument.

```kotlin
fun String.lastChar(): Char = this[this.length - 1]

// Java Call: StringExtKt.lastChar("ABC")
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using extensions for DSL-like syntax.

```kotlin
fun Int.isEven() = this % 2 == 0
println(10.isEven()) // Output: true
```

## 3. Kotlin Native (System / C-Interop)
Extensions on Native types (e.g., `CPointer`).

```kotlin
// fun CPointer<ByteVar>.toKString()
```

## 4. Multiplatform Path (KMP / Common)
Shared extensions for common types.

```kotlin
fun <T> List<T>.second(): T = this[1]
```

## 5. Explicit Path (Strictly Typed)
Extensions with explicit receiver types and nullability.

```kotlin
fun String?.isNullOrEmpty(): Boolean = this == null || this.isEmpty()
```

# The Logic Bridge
// Logic: Extensions do not actually modify the class they extend. They are "Syntactic Sugar" for static methods. The "Receiver" (the object the function is called on) is passed as a hidden parameter to the method at the JVM/Native layer.
