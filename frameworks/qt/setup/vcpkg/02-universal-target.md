# 🌍 Universal Setup: vcpkg Manifests (Official)

The industry-standard "Plug & Play" target system using **Triplets**.

---

## 1. 🏗️ The Triplet Strategy
A triplet defines the target architecture and OS. vcpkg uses this to select the correct NDK and Qt build flags.

| Target | Triplet | Support |
| :--- | :--- | :--- |
| **Android (ARM64)** | `arm64-android` | **Tested / Official** |
| **iOS (ARM64)** | `arm64-ios` | Community |
| **Windows** | `x64-windows` | Official |
| **Linux** | `x64-linux` | Official |

## 2. 📝 Building for Android
1.  **Set NDK path:** `export ANDROID_NDK_HOME=/path/to/ndk`.
2.  **Run CMake:**
```bash
cmake -B build-android \
  -DCMAKE_TOOLCHAIN_FILE=[vcpkg_root]/scripts/buildsystems/vcpkg.cmake \
  -DVCPKG_TARGET_TRIPLET=arm64-android
```

## 3. 🏁 The Logic Bridge
- **Plug & Play:** To switch from Windows to Android, you don't change a single line of code. You just change the `-DVCPKG_TARGET_TRIPLET` flag.
- **Isolation:** vcpkg installs the Android libraries in a separate folder (`vcpkg_installed/arm64-android`), preventing them from mixing with your host tools.

---

[➔ Back to Roadmap](../../usage/core/00-roadmap.md)
