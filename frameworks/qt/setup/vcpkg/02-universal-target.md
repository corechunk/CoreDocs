# 🌍 Universal Setup: vcpkg Manifests (Official)

The industry-standard "Plug & Play" target system using **Triplets**. This is **NOT** a different project; it is just your Desktop project with a different "Hardware Module" plugged in.

---

## 1. 🏗️ The Triplet Strategy
A triplet defines the target architecture and OS. vcpkg uses this to select the correct flags and build Qt for that specific environment.

| Target | Triplet | Support |
| :--- | :--- | :--- |
| **Android (ARM64)** | `arm64-android` | **Tested / Official** |
| **iOS (ARM64)** | `arm64-ios` | Community |
| **Windows** | `x64-windows` | Official |
| **Linux** | `x64-linux` | Official |

## 2. 🤖 Requirement: The NDK
Unlike libraries (which vcpkg downloads), the **Android NDK** is a system tool you must provide.
- **Path:** Usually in `$HOME/Android/Sdk/ndk/[version]`.
- **Note:** You only download it once. Your project "plugs it in" via an environment variable or a CMake cache variable.

## 3. 📝 Building for Android
You use the **exact same** `vcpkg.json` from your Desktop setup.

```bash
# 1. Provide the NDK path to your environment
export ANDROID_NDK_HOME=/path/to/ndk

# 2. Configure with the Android Triplet
cmake -B build-android \
  -DCMAKE_TOOLCHAIN_FILE=[vcpkg_root]/scripts/buildsystems/vcpkg.cmake \
  -DVCPKG_TARGET_TRIPLET=arm64-android
```

---

## 🏁 The Logic Bridge
- **Standard Location:** Keep your `vcpkg.json` in the **Project Root**.
- **Isolation:** vcpkg installs the Android libraries in `vcpkg_installed/arm64-android`, separate from your `x64-linux` binaries.
- **Recommendation:** Use [**CMake Presets**](../01-cmake-presets-dashboard.md) to automate the `ANDROID_NDK_HOME` and Triplet flags so you don't have to type them every time.

---

[➔ Back to Setup Hub](../README.md)
