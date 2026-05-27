# Fixed Arrays (CORE)

Definition: `Array<T>` represents a fixed-size collection of elements.

## 1. JVM-Legacy (Java-Interop Style)
JVM primitive arrays (e.g., `IntArray`).

```kotlin
val arr = IntArray(5)
```

## 2. Modern Kotlin (K2 / Idiomatic)
`arrayOf()` factory.

```kotlin
val arr = arrayOf(1, 2, 3)
```

## 3. Kotlin Native (System / C-Interop)
Native arrays mapped to C-memory.

```kotlin
val arr = intArrayOf(1, 2)
```

## 4. Multiplatform Path (KMP / Common)
Portable `Array`.

```kotlin
val arr = arrayOf("A", "B")
```

## 5. Explicit Path (Strictly Typed)
Explicitly typed array.

```kotlin
val arr: Array<Int> = arrayOf<Int>(10, 20)
```

# The Logic Bridge
// Logic: `Array<Int>` is an array of objects (Integer), while `IntArray` is an array of primitives (`int[]`), which is more memory-efficient on the JVM.
