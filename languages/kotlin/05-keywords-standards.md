# 05 - Keywords & Standards (CORE)

Definition: Keywords are reserved words in Kotlin. Standards define the language version and compiler behavior (e.g., Kotlin 2.0).

## 1. JVM-Legacy (Java-Interop Style)
Keywords shared with or mapping to JVM concepts.

```kotlin
public class Legacy {
    // 'public' is default in Kotlin but explicit here for JVM-style
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Kotlin-exclusive keywords like `when`, `suspend`, and `inline`.

```kotlin
fun main() {
    val x = 10
    when(x) {
        10 -> println("Match") // Output: Match
    }
}
```

## 3. Kotlin Native (System / C-Interop)
Keywords related to native interop.

```kotlin
// 'external' keyword for calling native functions
// external fun cFunction()
```

## 4. Multiplatform Path (KMP / Common)
KMP keywords `expect` and `actual`.

```kotlin
// expect fun getPlatform(): String
```

## 5. Explicit Path (Strictly Typed)
Handling soft keywords explicitly.

```kotlin
class Person {
    var name: String = ""
        get() = field
        set(value) { field = value }
}
```

# The Logic Bridge
// Logic: Kotlin uses "Hard Keywords" (always reserved) and "Soft Keywords" (context-dependent). This allows the language to evolve (adding features like `actual` or `expect`) without breaking existing code where those words might have been used as identifiers.
