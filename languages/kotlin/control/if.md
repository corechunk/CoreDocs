# If Conditional (CORE)

Definition: Binary choice structure. In Kotlin, `if` is an expression.

## 1. JVM-Legacy (Java-Interop Style)
`if` as a statement.

```kotlin
if (true) { println("OK") }
```

## 2. Modern Kotlin (K2 / Idiomatic)
`if` as an expression.

```kotlin
val res = if (10 > 5) "A" else "B"
```

## 3. Kotlin Native (System / C-Interop)
Checking native return codes.

```kotlin
if (result == 0) { }
```

## 4. Multiplatform Path (KMP / Common)
Portable `if`.

```kotlin
val x = if (true) 1 else 0
```

## 5. Explicit Path (Strictly Typed)
Explicit branches.

```kotlin
val s: String = if (true) { "Yes" } else { "No" }
```

# The Logic Bridge
// Logic: Since `if` is an expression, Kotlin does not need a ternary operator (`a ? b : c`).
