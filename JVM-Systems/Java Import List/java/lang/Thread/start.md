# Method: start()
## Class: `java.lang.Thread`

Causes this thread to begin execution; the Java Virtual Machine calls the `run` method of this thread.

### Signature
- **Inputs:** None
- **Returns:** `void`

### Description
The result is that two threads are running concurrently: the current thread (which returns from the call to the start method) and the other thread (which executes its run method).

### Example (Kotlin)
```kotlin
val thread = Thread { println("Running") }
thread.start()
```
