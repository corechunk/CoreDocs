# Method: newFixedThreadPool(int nThreads)
## Class: `java.util.concurrent.Executors`

Creates a thread pool that reuses a fixed number of threads.

### Signature
- **Inputs:** `nThreads: int` — Number of threads in the pool.
- **Returns:** `ExecutorService` — The created thread pool.

### Example (Kotlin)
```kotlin
val pool = Executors.newFixedThreadPool(4)
```
