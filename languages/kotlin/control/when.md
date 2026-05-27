# When Conditional (CORE)

Definition: Multi-branch choice. Replaces `switch`.

## 1. JVM-Legacy (Java-Interop Style)
Matching against constants.

```kotlin
when (x) {
    1 -> println("One")
    else -> println("Other")
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Pattern matching and ranges.

```kotlin
when (x) {
    in 1..10 -> println("Small")
    is String -> println("Text")
}
```

## 3. Kotlin Native (System / C-Interop)
Matching native types or codes.

```kotlin
when (errno) {
    EACCES -> println("Access denied")
}
```

## 4. Multiplatform Path (KMP / Common)
Portable `when`.

```kotlin
when {
    true -> println("True")
}
```

## 5. Explicit Path (Strictly Typed)
Exhaustive `when`.

```kotlin
val res: String = when (enum) {
    State.A -> "A"
    State.B -> "B"
}
```

# The Logic Bridge
// Logic: `when` is more flexible than `switch` and is verified for exhaustiveness by the compiler when used as an expression.
