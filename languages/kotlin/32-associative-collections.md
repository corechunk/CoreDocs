# 32 - Associative Collections (CORE - Hub)

Definition: Associative collections (Maps) store data as key-value pairs. Sets store unique elements. Like sequential collections, these are split into read-only and mutable versions.

## 1. JVM-Legacy (Java-Interop Style)
Using `java.util.HashMap` explicitly.

```kotlin
import java.util.HashMap

fun main() {
    val map = HashMap<String, Int>()
    map.put("Key", 1)
    println(map["Key"]) // Output: 1
}
```

## 2. Modern Kotlin (K2 / Idiomatic)
Using `mapOf()` and `setOf()` with the `to` infix function.

```kotlin
fun main() {
    val config = mapOf("host" to "localhost", "port" to 8080)
    val uniqueIds = setOf(1, 2, 2, 3)
    
    println(config["host"]) // Output: localhost
    println(uniqueIds)      // Output: [1, 2, 3]
}
```

## 3. Kotlin Native (System / C-Interop)
Native maps optimized for low-level performance.

```kotlin
fun main() {
    val nativeMap = mutableMapOf<Int, String>()
    nativeMap[0] = "Native"
    println(nativeMap[0]) // Output: Native
}
```

## 4. Multiplatform Path (KMP / Common)
Common interfaces for Maps and Sets.

```kotlin
fun main() {
    val commonMap: Map<Int, Boolean> = emptyMap()
    println(commonMap.isEmpty()) // Output: true
}
```

## 5. Explicit Path (Strictly Typed)
Explicitly defining map types and key-value pair types.

```kotlin
fun main() {
    val data: Map<String, String> = mapOf<String, String>(
        Pair("User", "Admin"),
        Pair("Role", "Super")
    )
    println(data) // Output: {User=Admin, Role=Super}
}
```

# The Logic Bridge
// Logic: The `to` in `mapOf("a" to 1)` is an **Infix Function** that creates a `Pair` object. While this looks like built-in syntax, it's actually part of the standard library. At the JVM level, `mapOf` often results in a `java.util.LinkedHashMap` to preserve insertion order.
