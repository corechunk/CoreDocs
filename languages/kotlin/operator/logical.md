# Logical Operators (CORE)

Definition: Operators for Boolean logic.

## 1. JVM-Legacy (Java-Interop Style)
`&&`, `||`, `!`.

```kotlin
val b = true && false
```

## 2. Modern Kotlin (K2 / Idiomatic)
Short-circuit evaluation.

```kotlin
val b = true || (10 / 0 == 0) // No error
```

## 3. Kotlin Native (System / C-Interop)
Native logical branching.

```kotlin
if (true && true) { }
```

## 4. Multiplatform Path (KMP / Common)
Portable logic.

```kotlin
val ok = !false
```

## 5. Explicit Path (Strictly Typed)
Explicit comparison.

```kotlin
val check: Boolean = (10 > 5) && (2 < 4)
```

# The Logic Bridge
// Logic: `&&` and `||` are short-circuiting, meaning the second operand is only evaluated if necessary.
