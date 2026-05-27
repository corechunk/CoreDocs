# Build Tools (PRO)

Definition: Tools like Gradle and Maven that automate the build lifecycle.

## 1. JVM-Legacy (Java-Interop Style)
Maven `pom.xml`.

```xml
<dependency>...</dependency>
```

## 2. Modern Kotlin (K2 / Idiomatic)
Gradle Kotlin DSL (`build.gradle.kts`).

```kotlin
dependencies { implementation(kotlin("stdlib")) }
```

## 3. Kotlin Native (System / C-Interop)
CLI tools and `cinterop`.

```bash
cinterop -def lib.def
```

## 4. Multiplatform Path (KMP / Common)
The KMP Gradle plugin.

```kotlin
kotlin { jvm(); linuxX64() }
```

## 5. Explicit Path (Strictly Typed)
Explicit toolchain configuration.

```kotlin
kotlin { jvmToolchain(17) }
```

# The Logic Bridge
// Logic: Build tools manage dependencies and coordinate compilation steps. Gradle is the standard for Kotlin, providing the flexibility needed for multiplatform targets.
