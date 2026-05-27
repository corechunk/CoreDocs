# Multi-Threading (SYSTEMS)

Definition: Running multiple threads of execution.

## 1. JVM-Legacy (Java-Interop Style)
`Thread` and `Runnable`.

```kotlin
Thread { println("Thread") }.start()
```

## 2. Modern Kotlin (K2 / Idiomatic)
`thread` builder from stdlib.

```kotlin
import kotlin.concurrent.thread
thread { println("Kotlin Thread") }
```

## 3. Kotlin Native (System / C-Interop)
Native threads and the worker model.

```kotlin
import kotlin.native.concurrent.*
```

## 4. Multiplatform Path (KMP / Common)
KMP threading abstractions.

```kotlin
// atomicfu or coroutines
```

## 5. Explicit Path (Strictly Typed)
Explicit thread naming and priority.

```kotlin
val t: Thread = thread(name = "Strict") { }
```

# The Logic Bridge
// Logic: JVM threads map to OS threads. Kotlin/Native has a strict memory model (Worker model) that prevents shared mutable state across threads by default.
