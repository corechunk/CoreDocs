# Memory Management (SYSTEMS)

Definition: Allocation and deallocation of memory.

## 1. JVM-Legacy (Java-Interop Style)
Garbage Collection (GC).

```kotlin
val obj = Any() // GC manages this
```

## 2. Modern Kotlin (K2 / Idiomatic)
ARC and GC internals.

```kotlin
// Kotlin/Native uses GC now (since 1.7)
```

## 3. Kotlin Native (System / C-Interop)
Manual memory in `memScoped`.

```kotlin
import kotlinx.cinterop.*
memScoped { val p = alloc<IntVar>() }
```

## 4. Multiplatform Path (KMP / Common)
Shared memory abstractions.

```kotlin
// no manual memory in commonMain
```

## 5. Explicit Path (Strictly Typed)
Explicit object pinning.

```kotlin
val pinned = obj.pin()
```

# The Logic Bridge
// Logic: JVM uses tracing GC. Kotlin/Native now uses a similar high-performance GC. Manual memory is only needed for C-interop.
