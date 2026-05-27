# HTTP Client API (PRO)

Definition: High-level API for web requests.

## 1. JVM-Legacy (Java-Interop Style)
`HttpURLConnection`.

```kotlin
val url = java.net.URL("http://google.com").openConnection()
```

## 2. Modern Kotlin (K2 / Idiomatic)
Ktor HTTP Client.

```kotlin
val client = HttpClient()
val res = client.get("http://google.com")
```

## 3. Kotlin Native (System / C-Interop)
Native HTTP engines (e.g., Curl, WinHttp).

```kotlin
val client = HttpClient(Curl)
```

## 4. Multiplatform Path (KMP / Common)
Ktor Client for KMP.

```kotlin
val client = HttpClient { }
```

## 5. Explicit Path (Strictly Typed)
Explicitly configured client.

```kotlin
val client: HttpClient = HttpClient(CIO)
```

# The Logic Bridge
// Logic: HTTP clients abstract the complexity of headers, body parsing, and connection pooling. Ktor uses platform-specific engines (OkHttp on Android, Curl on Linux) while providing a common API.
