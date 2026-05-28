# 🎛️ The Dashboard: CMake Presets

This is the **"Plug & Play"** heart of your project. `CMakePresets.json` allows you to switch between Windows, Android, and iOS targets without changing a single command.

---

## 1. 🧱 The Workflow
You define **Configure Presets** (for the SDKs) and **Build Presets** (for the compilers).

## 2. 📝 Example Dashboard (`CMakePresets.json`)
```json
{
  "version": 3,
  "configurePresets": [
    {
      "name": "windows-vcpkg",
      "displayName": "Windows (vcpkg)",
      "toolchainFile": "$env{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake",
      "binaryDir": "${sourceDir}/build-win",
      "cacheVariables": { "VCPKG_TARGET_TRIPLET": "x64-windows" }
    },
    {
      "name": "android-arm64",
      "displayName": "Android ARM64",
      "toolchainFile": "$env{ANDROID_NDK_ROOT}/build/cmake/android.toolchain.cmake",
      "binaryDir": "${sourceDir}/build-android",
      "cacheVariables": {
        "ANDROID_ABI": "arm64-v8a",
        "ANDROID_PLATFORM": "android-33"
      }
    }
  ]
}
```

## 3. 🚀 The "Plug & Play" Usage
To build for a different target, you just change the preset name:

```bash
# Build for Windows
cmake --preset windows-vcpkg
cmake --build --preset windows-vcpkg

# "Unplug" Windows, "Plug in" Android
cmake --preset android-arm64
cmake --build --preset android-arm64
```

---

[➔ Back to Roadmap](../../usage/core/00-roadmap.md)
