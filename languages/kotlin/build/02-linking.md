# Linking & Delivery (SYSTEMS)

Definition: Finalizing the binary and delivering the software.

## 1. JVM-Legacy (Java-Interop Style)
Fat JARs and `.class` files.

```bash
java -cp app.jar com.Main
```

## 2. Modern Kotlin (K2 / Idiomatic)
Shadow JARs or JPackage.

```bash
./gradlew shadowJar
```

## 3. Kotlin Native (System / C-Interop)
Static and dynamic linking of native binaries.

```bash
kotlinc-native main.kt -l mylib.static
```

## 4. Multiplatform Path (KMP / Common)
KMP library distribution (Klibs).

```bash
./gradlew publishToMavenLocal
```

## 5. Explicit Path (Strictly Typed)
Explicit manifest configuration.

```kotlin
tasks.jar { manifest { attributes["Main-Class"] = "MainKt" } }
```

# The Logic Bridge
// Logic: Linking resolves external references. On the JVM, this happens mostly at runtime (Dynamic), while Kotlin/Native supports both Static (included in binary) and Dynamic (resolved at runtime) linking.
