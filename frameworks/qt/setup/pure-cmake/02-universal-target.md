# 🌍 Universal Setup: Pure CMake (Official)

Manual cross-compilation management for Android and iOS targets.

---

## 1. 🤖 Android Requirements (Qt 6.11/6.8)
Qt is highly sensitive to NDK versions. ** r27c** is the standard for 2026.

| Requirement | Value |
| :--- | :--- |
| **NDK Version** | **r27c** (27.2.12479018) |
| **JDK Version** | **JDK 21+** |
| **SDK Platform** | Android 33 or 35 |

### Mandatory Environment Variables
```bash
export JAVA_HOME="/usr/lib/jvm/java-21-openjdk"
export ANDROID_SDK_ROOT="$HOME/Android/Sdk"
export ANDROID_NDK_ROOT="$ANDROID_SDK_ROOT/ndk/27.2.12479018"
```

## 2. 📝 The Build Command
You must provide the Android toolchain file to CMake:

```bash
cmake -B build-android \
  -DCMAKE_TOOLCHAIN_FILE=$ANDROID_NDK_ROOT/build/cmake/android.toolchain.cmake \
  -DANDROID_ABI=arm64-v8a \
  -DANDROID_PLATFORM=android-35 \
  -DQt6_DIR=$QT_ANDROID_PATH/lib/cmake/Qt6
```

## 3. 🍎 iOS Requirements
- **Hardware:** Strictly requires a Mac with **Xcode 16+**.
- **Toolchain:** Provided by Xcode (`xcode-select --install`).

### Build Command
```bash
cmake -B build-ios -G Xcode \
  -DCMAKE_SYSTEM_NAME=iOS \
  -DCMAKE_OSX_DEPLOYMENT_TARGET=17.0
```

---

[➔ Back to Setup Hub](../README.md)
