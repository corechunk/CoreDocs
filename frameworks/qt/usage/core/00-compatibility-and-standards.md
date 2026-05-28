# ⚖️ Qt & C++ Compatibility (2026 Official)

This document codifies the "Source of Truth" for version compatibility and language standards as of May 2026.

---

## 1. 🎯 Target Versions
| Version | Support Type | Release Date | Support End |
| :--- | :--- | :--- | :--- |
| **Qt 6.11** | Current / Latest | March 2026 | Sept 2026 |
| **Qt 6.8** | **LTS (Long Term)** | Oct 2024 | Oct 2029 |

## 2. ⚙️ C++ Standard Requirements
Qt 6 is a modern framework designed to leverage recent C++ evolutions.

- **Baseline:** **C++17** (Mandatory for all Qt 6 modules).
- **Modern Hub:** **C++20** (Highly Recommended).
    - **Requirement:** **Qt WebEngine** strictly requires C++20 due to its Chromium core.
    - **Features:** Enables `operator<=>` (Spaceship) and `std::span` (via `QSpan`) integration.
- **Future-Proof:** **C++23** (Supported).
    - Fully compatible with Qt 6.11 for advanced systems engineering.

## 3. 🛠️ Compiler Minimums
To build Qt 6.11/6.8, your toolchain must meet these minimums:

| Platform | Compiler | Min Version | Recommended |
| :--- | :--- | :--- | :--- |
| **Windows** | MSVC | 2019 (16.x) | **MSVC 2022** |
| | MinGW | 11.2 | 13.x+ |
| **Linux** | GCC | 9.0 | **11.0+** |
| | Clang | 12.0 | **15.0+** |
| **macOS** | Apple Clang | Xcode 14 | **Xcode 16** |
| **Android** | NDK | r25b | **r26+** |

## 4. 🚀 Why C++20 with Qt 6?
*   **Three-way Comparison:** Qt classes like `QDate`, `QTime`, and `QString` use `operator<=>` for faster, more idiomatic sorting and comparison.
*   **Concepts:** Internal Qt headers use concepts to provide more readable compiler errors when you pass wrong types to templates.
*   **Standard Library Interop:** Better alignment between `QStringView` and `std::string_view`, and `QList` and `std::vector`.

---

[➔ Back to Roadmap](./00-roadmap.md)
