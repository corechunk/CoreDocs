# 🎛️ The Dashboard: CMake Presets

This is the **"Physical Switch"** of your project. `CMakePresets.json` maps your high-level intent (e.g., "Build for Android") to the specific technical requirements (Triplets, SDK paths, Toolchains).

---

## 1. 🧱 The Workflow
1.  **Librarian (vcpkg):** Downloads the libraries.
2.  **Hardware (NDK/SDK):** You provide the path to where you downloaded the NDK.
3.  **The Switch (Presets):** Connects the two.

---

## 📝 2. Example: One Dashboard, Multiple Lives
This file lives in your **Project Root**. It allows you to "unplug" the Desktop environment and "plug in" Android without touching a single C++ line.

```json
{
  "version": 3,
  "configurePresets": [
    {
      "name": "desktop-vcpkg",
      "displayName": "Linux Desktop (vcpkg)",
      "toolchainFile": "$env{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake",
      "binaryDir": "${sourceDir}/build-desktop",
      "cacheVariables": { "VCPKG_TARGET_TRIPLET": "x64-linux" }
    },
    {
      "name": "android-vcpkg",
      "displayName": "Android ARM64 (vcpkg)",
      "toolchainFile": "$env{VCPKG_ROOT}/scripts/buildsystems/vcpkg.cmake",
      "binaryDir": "${sourceDir}/build-android",
      "cacheVariables": {
        "VCPKG_TARGET_TRIPLET": "arm64-android",
        "ANDROID_NDK_HOME": "$env{HOME}/Android/Sdk/ndk/27.2.12479018",
        "CMAKE_SYSTEM_NAME": "Android",
        "ANDROID_PLATFORM": "android-33"
      }
    }
  ]
}
```

## 3. 🚀 Using the Switch
Once this file is in your root, building becomes a simple choice:

```bash
# Target: Linux Desktop
cmake --preset desktop-vcpkg
cmake --build --preset desktop-vcpkg

# Target: Android (Plug & Play!)
cmake --preset android-vcpkg
cmake --build --preset android-vcpkg
```

---

[➔ Back to Setup Hub](./README.md)
