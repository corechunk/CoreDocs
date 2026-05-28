# 🏗️ Qt Setup: The Engine Room

The "Engine Room" is the architectural heart of your Qt project. It is responsible for managing SDKs and cross-platform targets without polluting your host system.

---

## 🧠 1. The Core Architecture (Top 2 Redirections)
Before implementing a setup, you must master the **Mindset** and the **Mechanism**.

1.  [**Universal Strategy (The Mindset)**](./00-universal-strategy.md)  
    *   **Purpose:** Explains the **"Plug & Play"** philosophy.
    *   **Logic:** Treat SDKs (Android NDK, Windows SDK) as modular hardware units that you "plug into" your project environment, not your OS.

2.  [**The Dashboard (The Mechanism)**](./01-cmake-presets-dashboard.md)  
    *   **Purpose:** Explains **`CMakePresets.json`**.
    *   **Logic:** Acts as the "Physical Switch" that toggles your environment between Desktop, Android, or iOS with a single command.

---

## 🛠️ 2. Environment Orchestration (The Methods)
Choose your "Librarian" for fetching and building Qt and its dependencies.

### 🏗️ [**Pure CMake (Manual)**](./pure-cmake/01-standard-qt.md)
*   **Use Case:** Rapid prototyping or system-tied tools.
*   **Logic:** You manually tell CMake where Qt is.
*   **Path:** [➔ Standard (Desktop)](./pure-cmake/01-standard-qt.md) | [➔ Universal (Android/iOS)](./pure-cmake/02-universal-target.md)

### 📦 [**vcpkg Manifests (Industry Standard)**](./vcpkg/01-standard-qt.md)
*   **Use Case:** Professional, cross-platform apps with heavy dependencies.
*   **Logic:** Qt is a "Package" defined in `vcpkg.json`.
*   **Path:** [➔ Standard (Desktop)](./vcpkg/01-standard-qt.md) | [➔ Universal (Android/iOS)](./vcpkg/02-universal-target.md)

### ❄️ [**Nix Flakes (Elite/Isolated)**](./nix/01-standard-qt.md)
*   **Use Case:** Linux-first development with zero system pollution.
*   **Logic:** 100% reproducible, isolated build shells.
*   **Path:** [➔ Standard (Desktop)](./nix/01-standard-qt.md) | [➔ Universal (Android/iOS)](./nix/02-universal-target.md)

---

## 🎯 Selection Matrix: What should I choose?

| If you are... | And you want... | Choose... |
| :--- | :--- | :--- |
| **A Beginner** | Quick start on your current OS | **Pure CMake** |
| **A Professional** | To build for Windows & Android | **vcpkg** |
| **A Linux Purist** | Zero system pollution | **Nix Flakes** |
| **A Cross-Platformer** | One command to switch targets | **CMake Presets** |

---

[➔ Back to Qt Hub](../README.md)
