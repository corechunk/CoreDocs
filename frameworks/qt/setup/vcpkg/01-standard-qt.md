# 📦 Standard Qt Setup: vcpkg Manifests (Official)

Automated, manifest-based library management for C++20/23 projects.

---

## 1. 📝 The Manifest (`vcpkg.json`)
The manifest ensures your team always uses the exact same version of Qt.

```json
{
  "name": "qt-vcpkg-project",
  "version": "1.0.0",
  "dependencies": [
    "qtbase",
    "qtdeclarative",
    "qtsvg"
  ]
}
```

## 2. ⚙️ Configuration
Run CMake with the vcpkg toolchain. vcpkg will automatically detect the manifest and build Qt.

```bash
cmake -B build -S . \
  -DCMAKE_TOOLCHAIN_FILE=[vcpkg_root]/scripts/buildsystems/vcpkg.cmake
```

## 3. 🏁 The Logic Bridge
- **Binary Cache:** vcpkg only builds Qt once. It saves the binary in your local cache (`~/.cache/vcpkg`) for instant use in other projects.
- **`find_package`**: Works exactly the same as Pure CMake. vcpkg transparently handles the library paths.

---

[➔ Back to Setup Hub](../README.md)
