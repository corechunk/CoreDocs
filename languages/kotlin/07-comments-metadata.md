# 07 - Comments & Metadata (CORE)

Definition: Comments provide human-readable documentation. Metadata is handled via Annotations and KDoc.

## 1. JVM-Legacy (Java-Interop Style)
Standard comments and `@JvmStatic` style annotations.

```kotlin
class Legacy {
    @JvmField val id = 1
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using KDoc for documentation.

```kotlin
/**
 * Main entry point.
 */
fun main() {
    println("Doc'd") // Output: Doc'd
}
```

## 3. Kotlin Native (System / C-Interop)
Native-specific annotations like `@CName`.

```kotlin
// @CName("native_func")
// fun nativeFunc() { }
```

## 4. Multiplatform Path (KMP / Common)
Common annotations like `@Throws` (platform-mapped).

```kotlin
@Throws(Exception::class)
fun fail() { }
```

## 5. Explicit Path (Strictly Typed)
Explicitly using `@file` level annotations.

```kotlin
@file:JvmName("Utils")
package core
```

# The Logic Bridge
// Logic: Annotations are metadata processed by the compiler or at runtime. In Kotlin/Native, annotations like `@CName` affect the symbol name in the generated binary, while KDoc is processed by Dokka to generate universal documentation.
