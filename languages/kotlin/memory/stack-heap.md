# Stack vs Heap (SYSTEMS)

Definition: Two primary memory regions for data storage.

## 1. JVM-Legacy (Java-Interop Style)
Primitives on stack, objects on heap.

```kotlin
val x = 10 // Stack
val s = "A" // Heap
```

## 2. Modern Kotlin (K2 / Idiomatic)
Escape analysis optimizations.

```kotlin
// Compiler may optimize small objects
```

## 3. Kotlin Native (System / C-Interop)
Stack allocation in Native code.

```kotlin
// local variables in Native are on stack
```

## 4. Multiplatform Path (KMP / Common)
Abstract memory model.

```kotlin
// Target specific placement
```

## 5. Explicit Path (Strictly Typed)
Explicitly managing large heap allocations.

```kotlin
val largeArr = IntArray(1_000_000)
```

# The Logic Bridge
// Logic: The stack is for fast, short-lived data; the heap is for dynamic, long-lived data. Kotlin abstracts this, but it's critical for performance tuning.
