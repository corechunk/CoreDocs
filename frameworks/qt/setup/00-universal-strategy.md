# ❄️ Universal Strategy: The Plug & Play Philosophy

The "Source of Truth" for managing multiple Operating System targets from a single C++ codebase.

---

## 1. 🏗️ The Problem: Environment Pollution
Traditional cross-platform development is messy:
- You install the Android NDK in `/home/user/Android`.
- You install Qt for Windows in `C:\Qt`.
- You set 10 different environment variables that conflict between projects.

## 2. 🧱 The Solution: The Plug & Play Model
In a **Universal Target System**, you treat SDKs like "Hardware Modules" that you plug into your project only when needed.

### The Trio of Control
1.  **CMake (The Engine):** Your C++ logic. It doesn't care what OS it's on.
2.  **vcpkg/Nix (The Librarian):** These tools "fetch" the correct version of Qt and other libraries for your specific target.
3.  **CMake Presets (The Switch):** A single JSON file that toggles between "Hardware Modules" (Windows, Android, Linux).

---

## 📂 3. Project Anatomy: Where do files go?
To avoid the "Maze," follow this standard structure. You are free to choose other locations, but this is the **industry standard**.

```text
MyQtProject/
├── CMakeLists.txt         # Your top-level build script (The Engine)
├── CMakePresets.json      # The Switch (Targets & SDK paths)
├── vcpkg.json             # The Librarian (List of required libraries)
├── vcpkg-configuration.json # (Optional) Version locking
├── flake.nix              # (If using Nix) The isolated shell
└── src/                   # Your actual C++ code (.cpp, .h)
    └── main.cpp
```

## 🌍 4. One Codebase, Many Triplets
You do **not** create separate projects for Desktop and Android. You use **one** project and tell your "Librarian" (vcpkg/Nix) which **Triplet** to use.

- **Triplet:** A name for a target platform (e.g., `x64-linux`, `arm64-android`).
- **Logic:** You run the *exact same* project, but you plug in the `arm64-android` triplet when you want to build for your phone.

---

[➔ Back to Setup Hub](./README.md)
