# 🛠️ STL System Utilities - Master Reference

## 1. The Objective
The Standard Library provides powerful tools for interacting with the OS and handling common data formats like time, regular expressions, and file paths.

---

## 2. Visual Logic
- **`std::filesystem`:** A cross-platform way to handle `C:\Paths` vs `/unix/paths`.
- **`std::chrono`:** High-precision timers for performance measuring.
- **`std::format`:** Modern, safe string formatting (C++20).

---

## 3. # The Logic Bridge (Key Points)

- **Filesystem (C++17):** Replaces messy C-style `stat` and `dirent`. It allows iterating through directories and checking file sizes with a clean object-oriented API.
- **Chrono:** Use `steady_clock` for measuring execution time (it never goes backward) and `system_clock` for real-world dates/times.
- **Regex:** Provides powerful pattern matching, but be careful—it has a high performance cost compared to simple string searches.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <filesystem>
#include <chrono>
#include <regex>

namespace fs = std::filesystem;

int main() {
    // --- 1. FILESYSTEM (C++17) ---
    fs::path p = "test.txt";
    if (fs::exists(p)) {
        std::cout << "Size: " << fs::file_size(p) << "\n";
    }

    // --- 2. CHRONO (Timing) ---
    auto start = std::chrono::steady_clock::now();
    // ... do work ...
    auto end = std::chrono::steady_clock::now();
    auto diff = end - start;
    std::cout << "Took: " << std::chrono::duration<double, std::milli>(diff).count() << "ms\n";

    // --- 3. REGEX ---
    std::string email = "test@corechunk.ai";
    std::regex pattern(R"(\w+@\w+\.\w+)");
    if (std::regex_match(email, pattern)) {
        std::cout << "Valid email!\n";
    }

    return 0;
}
```

---
[➔ Back to STL Hub](00-stl-overview.md)
