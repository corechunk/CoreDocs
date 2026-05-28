# 🏗️ Standard Qt Setup: Pure CMake (Official)

Manual path management for local desktop development using official Qt binaries.

---

## 1. ⚙️ Prerequisites
- **Windows:** Qt Online Installer + **MSVC 2022** or **MinGW 13+**.
- **Linux:** `sudo pacman -S qt6-base qt6-declarative` (Arch) or equivalent.
- **macOS:** `brew install qt6` or Online Installer.

## 2. 📝 CMake Configuration
To find a manually installed Qt, you must point CMake to the configuration files.

```cmake
cmake_minimum_required(VERSION 3.20)
project(StandardQtApp)

# 1. Set the Path (if not in system path)
# set(CMAKE_PREFIX_PATH "C:/Qt/6.8.0/msvc2022_64")

# 2. Find Packages
find_package(Qt6 REQUIRED COMPONENTS Core Gui Widgets)

# 3. Standard Qt 6 Executable Logic
qt_add_executable(StandardQtApp main.cpp)

# 4. Link Libraries
target_link_libraries(StandardQtApp PRIVATE Qt6::Widgets)
```

## 3. 🔍 The Logic Bridge
- **`find_package`**: Looks for `Qt6Config.cmake`. If you have multiple versions, `CMAKE_PREFIX_PATH` determines which one is selected first.
- **`qt_add_executable`**: A Qt-specific wrapper for `add_executable` that handles icon embedding and deployment logic automatically.

---

[➔ Back to Roadmap](../../usage/core/00-roadmap.md)
