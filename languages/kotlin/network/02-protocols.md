# Protocols: TCP & UDP (SYSTEMS)

Definition: Connection-oriented (TCP) and connectionless (UDP) protocols.

## 1. JVM-Legacy (Java-Interop Style)
`ServerSocket` and `DatagramSocket`.

```kotlin
val server = java.net.ServerSocket(8080)
```

## 2. Modern Kotlin (K2 / Idiomatic)
Ktor Server with Netty/CIO.

```kotlin
// embeddedServer(Netty) { }.start()
```

## 3. Kotlin Native (System / C-Interop)
Native TCP/UDP implementations.

```kotlin
// bind(), listen(), accept()
```

## 4. Multiplatform Path (KMP / Common)
KMP network libraries.

```kotlin
// Ktor CIO
```

## 5. Explicit Path (Strictly Typed)
Explicit protocol handling.

```kotlin
val tcp: java.net.Socket = java.net.Socket()
```

# The Logic Bridge
// Logic: TCP ensures reliable delivery via handshakes, while UDP is faster but unreliable. Kotlin's Ktor framework provides a unified DSL for both.
