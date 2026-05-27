# 01 - Compilation & Execution (CORE)

Definition: Compilation is the process of converting Kotlin source code (`.kt`) into an executable format. For the JVM, this is `.class` (Bytecode). Execution is the process of running that code.

## 1. JVM-Legacy (Manual kotlinc)
Compiling and running using the command line tools directly.

```bash
# COMPILE
kotlinc hello.kt -include-runtime -d hello.jar

# RUN
java -jar hello.jar
# Output: Hello, Kotlin!
```

## 2. Modern Kotlin (Gradle KTS)
Running via Gradle, which handles dependencies and incremental compilation.

```bash
# RUN VIA GRADLE
./gradlew run

# Output: 
# > Task :run
# Hello, Kotlin!
```

## 3. Multiplatform Path (Native Build)
Compiling to a native executable.

```bash
# COMPILE TO NATIVE
kotlinc-native hello.kt -o hello

# RUN NATIVE
./hello.kexe
# Output: Hello, Kotlin!
```

## 4. Explicit Path (K2 Compiler)
Explicitly enabling the K2 compiler for a build.

```bash
# CLI FLAG
kotlinc -language-version 2.0 hello.kt

# Output: (Compilation Success)
```

# The Logic Bridge
// Logic: The Kotlin compiler (`kotlinc`) does not produce machine code for the JVM; it produces Bytecode that the JVM's JIT (Just-In-Time) compiler then converts to machine code during execution. Kotlin 2.0 (K2) features a completely rewritten frontend that is significantly faster and provides more accurate error messages.
