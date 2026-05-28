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
2.  **vcpkg/Nix (The Librarian):** These tools "fetch" the correct SDK (Android, iOS, Win) and put them in a temporary box for the project.
3.  **CMake Presets (The Switch):** A single JSON file (`CMakePresets.json`) that provides the "Buttons" to switch between targets.

## 3. 🏁 The Logic Bridge
- **No Global Installs:** You never install an SDK "to the system." You always install it "to the project environment."
- **One Source, All Binaries:** The exact same C++ `main.cpp` produces a `.exe`, a `.apk`, and a `.app` just by switching the environment manager's target.

---

[➔ Back to Roadmap](../usage/core/00-roadmap.md)
