# 🟢 Standard: I/O Streams [CORE]

## Definition
C++ uses **Iostreams** (`std::cin`, `std::cout`, `std::cerr`) for high-level, type-safe input and output.

## 1. Legacy Way (C++11 / C++17)
Standard usage of `std::cout` and `std::cerr`.

```cpp
#include <iostream>

int main() {
    std::cout << "Normal Output\n"; // Output: Normal Output
    std::cerr << "Error Output\n";  // Output: Error Output
    return 0;
}
```

## 2. Modern Way (C23)
Using C++23 **`std::print`** for faster, modern formatting.

```cpp
#include <print> // C++23

int main() {
    // std::print: Native C++23 (faster than iostreams)
    std::print("Normal Output\n"); // Output: Normal Output
    std::print(stderr, "Error Output\n"); // Output: Error Output
    return 0;
}
```

# The Logic Bridge
// Logic: `std::cout` is an object that overloads `operator<<` for every type, performing formatting at runtime. `std::print` (C++23) uses `std::format` logic to perform type-safe formatting with lower overhead.
