# 10 - String Escaping (CORE)

Definition: Escaping allows representing special characters within strings.

## 1. JVM-Legacy (Java-Interop Style)
Standard backslash escaping.

```kotlin
val s = "Line\nBreak"
```

## 2. Modern Kotlin (K2 / Idiomatic)
Triple-quoted raw strings.

```kotlin
val raw = """
    No \n needed
""".trimIndent()
```

## 3. Kotlin Native (System / C-Interop)
Escaping in strings passed to C-functions.

```kotlin
import platform.posix.*

fun main() {
    printf("Native\tTab\n") // Output: Native	Tab
}
```

## 4. Multiplatform Path (KMP / Common)
Consistent escaping across targets.

```kotlin
val path = "C:\\Path"
```

## 5. Explicit Path (Strictly Typed)
Unicode escapes.

```kotlin
val heart: String = "\u2764"
```

# The Logic Bridge
// Logic: Escaped characters are resolved into single tokens during lexing. Raw strings are stored literally in the binary, preserving all characters including newlines, making them ideal for multi-line text or regex patterns.
