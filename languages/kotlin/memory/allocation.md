# Memory Allocation (SYSTEMS)

Definition: Requesting memory from the OS.

## 1. JVM-Legacy (Java-Interop Style)
`new` keyword (implicit in Kotlin).

```kotlin
val obj = Object()
```

## 2. Modern Kotlin (K2 / Idiomatic)
Factory functions.

```kotlin
val list = mutableListOf<Int>()
```

## 3. Kotlin Native (System / C-Interop)
POSIX `malloc` and `free`.

```kotlin
import platform.posix.*
val p = malloc(1024u)
free(p)
```

## 4. Multiplatform Path (KMP / Common)
Shared allocation logic.

```kotlin
// Target specific impls
```

## 5. Explicit Path (Strictly Typed)
Explicitly typed allocation.

```kotlin
val buffer: ByteBuffer = ByteBuffer.allocateDirect(1024)
```

# The Logic Bridge
// Logic: Most allocations in Kotlin are managed by the runtime. Direct allocation is reserved for high-performance or low-level interop scenarios.
