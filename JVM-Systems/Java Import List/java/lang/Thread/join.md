# Method: join()
## Class: `java.lang.Thread`

Waits for this thread to die.

### Signature
- **Inputs:** None
- **Returns:** `void`

### Description
Useful for synchronizing threads. Calling `join()` on a thread will block the current thread until the target thread finishes its execution.

### Example (Kotlin)
```kotlin
val thread = Thread { ... }
thread.start()
thread.join() // Main thread waits here
```
