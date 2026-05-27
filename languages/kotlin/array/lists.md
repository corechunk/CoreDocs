# Lists (CORE)

Definition: `List` (read-only) and `MutableList` (modifiable) are the primary sequential collections.

## 1. JVM-Legacy (Java-Interop Style)
`ArrayList`.

```kotlin
val list = java.util.ArrayList<Int>()
```

## 2. Modern Kotlin (K2 / Idiomatic)
`listOf()`, `mutableListOf()`.

```kotlin
val list = listOf(1, 2)
```

## 3. Kotlin Native (System / C-Interop)
Native list implementation.

```kotlin
val list = mutableListOf<String>()
```

## 4. Multiplatform Path (KMP / Common)
Common `List` interface.

```kotlin
val list: List<Int> = listOf(1)
```

## 5. Explicit Path (Strictly Typed)
Explicit types.

```kotlin
val list: MutableList<Int> = mutableListOf<Int>(10)
```

# The Logic Bridge
// Logic: `List` is a read-only interface. At runtime, it's usually an `ArrayList`, but the compiler prevents write access.
