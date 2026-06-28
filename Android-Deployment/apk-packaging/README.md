# 📦 APK Staging & Directory Layout

To deploy native code inside a standard Android app, you must bundle compiled shared libraries (`.so`) within the Android Application Package (APK) file structure.

---

### 1. APK Directory Structure

An APK file is a standard ZIP archive. At runtime, the Android OS looks inside the `lib/` directory to load native compiled code. The directories inside `lib/` match the target device's CPU architecture:

```text
my_application.apk (ZIP Archive)
├── AndroidManifest.xml   <-- App metadata, permissions, package declaration
├── classes.dex           <-- Java/Kotlin bytecode for the Android runtime (Dalvik)
└── lib/                  <-- Staging directory for native binary assets
    ├── arm64-v8a/        <-- Directory for 64-bit ARM shared libraries
    │   └── libnative.so  <-- Compiled native library file
    ├── armeabi-v7a/      <-- Directory for 32-bit ARM shared libraries
    │   └── libnative.so
    └── x86_64/           <-- Directory for x86_64 emulator shared libraries
        └── libnative.so
```

---

### 2. Gradle Build Integration

If you use Android Studio and Gradle, you place your source files in `app/src/main/cpp/` and link them via a `CMakeLists.txt` script. Gradle automatically handles compiler triplets and places the output files in their correct folders inside the APK.

```groovy
// app/build.gradle
android {
    defaultConfig {
        externalNativeBuild {
            cmake {
                // Select target compilation architectures (ABIs)
                abiFilters "arm64-v8a", "x86_64"
            }
        }
    }
    externalNativeBuild {
        cmake {
            path file("src/main/cpp/CMakeLists.txt")
            version "3.22.1"
        }
    }
}
```

---

### 🗺️ Redirection Directory

*   📄 [**`signing-and-alignment.md`**](./signing-and-alignment.md) — How to package, align, and sign APK files for production deployment.
