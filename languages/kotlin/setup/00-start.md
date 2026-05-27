# 00 - Start (CORE)

Definition: The Kotlin toolchain consists of the compiler (`kotlinc`), build tools (Gradle), and runtime environments. For modern development, `mise` is used to manage versions, and the K2 compiler is the current standard for performance.

## 1. JVM-Legacy (Manual Installation)
Installing the standalone Kotlin compiler and running manually.

```bash
# INSTALL (Manual)
# sudo pacman -S kotlin

# VERSION CHECK
kotlinc -version
# Output: info: Kotlin Compiler version 2.0.0
```

## 2. Modern Kotlin (Mise & SDKMAN)
Using `mise` to manage project-specific Kotlin and Java versions.

```bash
# MISE SETUP
mise use kotlin@latest
mise use java@openjdk-21

# Output: using kotlin 2.0.0, java 21.0.2
```

## 3. Multiplatform Path (KMP Tooling)
Using Kotlin/Native and cross-platform targets.

```bash
# Check Kotlin/Native compiler
kotlinc-native -version
# Output: info: Kotlin/Native 2.0.0
```

## 4. Explicit Path (Gradle Configuration)
Defining the toolchain explicitly in `build.gradle.kts`.

```kotlin
kotlin {
    jvmToolchain(21)
}
// Logic: Ensures every developer uses the same Java version for compilation.
```

# The Logic Bridge
// Logic: The Kotlin toolchain is designed to be cross-platform. While `kotlinc` targets the JVM, `kotlinc-native` uses the LLVM backend to compile Kotlin code directly into machine-specific binaries (e.g., `.exe`, `.so`, or Mach-O), allowing Kotlin to run without a VM on target platforms.
