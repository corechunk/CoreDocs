# Assignment Operators (CORE)

Definition: Operators for assigning values and performing combined operations.

## 1. JVM-Legacy (Java-Interop Style)
`=`, `+=`, `-=`, etc.

```kotlin
var x = 10
x += 5
```

## 2. Modern Kotlin (K2 / Idiomatic)
Assignment as a statement (does not return a value).

```kotlin
var x = 0
x = 10
```

## 3. Kotlin Native (System / C-Interop)
Assigning to native memory/pointers.

```kotlin
// ptr.pointed.value = 10
```

## 4. Multiplatform Path (KMP / Common)
Standard assignment.

```kotlin
var s = "A"
s += "B"
```

## 5. Explicit Path (Strictly Typed)
Explicit typed assignment.

```kotlin
var count: Int = 0
count = count + 1
```

# The Logic Bridge
// Logic: Assignment in Kotlin is a statement, not an expression, to prevent bugs like `if (a = b)`.
