# Multi-File Projects (PRO)

Definition: Organizing code across multiple files and packages.

## 1. JVM-Legacy (Java-Interop Style)
Standard package structure.

```kotlin
package com.example.app
```

## 2. Modern Kotlin (K2 / Idiomatic)
Modular project structure with Gradle.

```kotlin
// src/commonMain/kotlin
```

## 3. Kotlin Native (System / C-Interop)
Linking multiple native sources.

```kotlin
// kotlinc-native main.kt utils.kt
```

## 4. Multiplatform Path (KMP / Common)
Shared code across modules.

```kotlin
// expect/actual pattern
```

## 5. Explicit Path (Strictly Typed)
Explicit imports.

```kotlin
import com.example.Utils.helper
```

# The Logic Bridge
// Logic: Kotlin uses packages for logical grouping. The compiler links these files into a single binary or JAR.
