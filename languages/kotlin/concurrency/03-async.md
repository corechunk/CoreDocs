# Async & Coroutines (PRO)

Definition: Non-blocking asynchronous programming using coroutines.

## 1. JVM-Legacy (Java-Interop Style)
`CompletableFuture` or `Callbacks`.

```kotlin
// java.util.concurrent.CompletableFuture
```

## 2. Modern Kotlin (K2 / Idiomatic)
`suspend` functions and `async`/`await`.

```kotlin
suspend fun fetch() = "Data"
```

## 3. Kotlin Native (System / C-Interop)
Native coroutines on the main loop.

```kotlin
// GlobalScope.launch { }
```

## 4. Multiplatform Path (KMP / Common)
`kotlinx.coroutines` for shared async code.

```kotlin
suspend fun common() { }
```

## 5. Explicit Path (Strictly Typed)
Explicit CoroutineScope and Dispatchers.

```kotlin
val scope = CoroutineScope(Dispatchers.Default)
```

# The Logic Bridge
// Logic: Coroutines are "lightweight threads" managed by the Kotlin runtime, not the OS. They use a state-machine transformation to suspend and resume execution without blocking threads.
