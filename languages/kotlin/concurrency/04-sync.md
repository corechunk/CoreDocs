# Synchronization (SYSTEMS)

Definition: Managing access to shared resources across threads.

## 1. JVM-Legacy (Java-Interop Style)
`synchronized` keyword and blocks.

```kotlin
@Synchronized fun sync() { }
```

## 2. Modern Kotlin (K2 / Idiomatic)
`Mutex` from coroutines.

```kotlin
val mutex = Mutex()
```

## 3. Kotlin Native (System / C-Interop)
Native atomic types and locks.

```kotlin
import kotlin.native.concurrent.AtomicInt
```

## 4. Multiplatform Path (KMP / Common)
Atomicfu for cross-platform atomics.

```kotlin
// AtomicInt(0)
```

## 5. Explicit Path (Strictly Typed)
Explicit lock usage.

```kotlin
val lock = java.util.concurrent.locks.ReentrantLock()
```

# The Logic Bridge
// Logic: Synchronization prevents race conditions. JVM uses monitor locks, while Native uses platform-specific atomic operations and mutexes.
