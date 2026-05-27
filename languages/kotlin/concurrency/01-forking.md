# Process Forking (SYSTEMS)

Definition: Managing external processes.

## 1. JVM-Legacy (Java-Interop Style)
`ProcessBuilder`.

```kotlin
val p = ProcessBuilder("ls").start()
```

## 2. Modern Kotlin (K2 / Idiomatic)
Kotlin wrappers for process execution.

```kotlin
// Runtime.getRuntime().exec("ls")
```

## 3. Kotlin Native (System / C-Interop)
Using POSIX `fork` and `exec`.

```kotlin
import platform.posix.*
// fork()
```

## 4. Multiplatform Path (KMP / Common)
KMP libraries for process management.

```kotlin
// platform specific expect/actual
```

## 5. Explicit Path (Strictly Typed)
Explicit process handling.

```kotlin
val proc: Process = ProcessBuilder("echo").start()
```

# The Logic Bridge
// Logic: Process management is platform-specific. JVM uses `java.lang.Process`, while Native uses direct OS syscalls.
