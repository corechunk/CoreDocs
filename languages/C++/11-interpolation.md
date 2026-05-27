# 🟢 Standard: Interpolation (Formatting) [CORE]

## Definition
C++ has evolved from `std::cout` (stream-based) and `printf` (C-style) to **`std::format`** (C++20/23), which is safer and faster.

## 1. Legacy Way (C++11 / C++17)
Using iostreams with manipulators.

```cpp
#include <iostream>
#include <iomanip>

int main() {
    int id = 101;
    double val = 3.14159;

    std::cout << "ID: " << id << " Val: " << std::fixed << std::setprecision(2) << val << "\n";
    // Output: ID: 101 Val: 3.14
    return 0;
}
```

## 2. Modern Way (C23)
Using `std::format` or `std::print` (C++23) for Python-style interpolation.

```cpp
#include <iostream>
#include <print> // C++23

int main() {
    auto id = 101;
    auto val = 3.14159;

    // std::print: C++23 native printing with formatting
    std::print("ID: {} Val: {:.2f}\n", id, val);
    // Output: ID: 101 Val: 3.14
    return 0;
}
```

# The Logic Bridge
// Logic: `std::format` is checked at compile-time for type safety. It generates a specialized formatting function that is significantly faster than the runtime parsing done by `printf`.
