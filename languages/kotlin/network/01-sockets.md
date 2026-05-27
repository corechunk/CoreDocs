# Socket Basics (SYSTEMS)

Definition: Low-level network communication.

## 1. JVM-Legacy (Java-Interop Style)
`java.net.Socket`.

```kotlin
val s = java.net.Socket("localhost", 80)
```

## 2. Modern Kotlin (K2 / Idiomatic)
Ktor Raw Sockets.

```kotlin
// selectorManager.socket().connect()
```

## 3. Kotlin Native (System / C-Interop)
POSIX sockets.

```kotlin
import platform.posix.*
// socket(AF_INET, SOCK_STREAM, 0)
```

## 4. Multiplatform Path (KMP / Common)
Ktor sockets for KMP.

```kotlin
// aSocket(selector).tcp().connect(...)
```

## 5. Explicit Path (Strictly Typed)
Explicit socket configuration.

```kotlin
val s: java.net.Socket = java.net.Socket()
```

# The Logic Bridge
// Logic: Sockets provide the base layer for TCP/UDP communication. JVM abstracts these via `java.net`, while Native requires direct interaction with the OS socket API.
