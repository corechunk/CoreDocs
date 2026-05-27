# 🔴 Standard: Floating Point [SYSTEMS]

## Definition
Decimals in C++ use IEEE 754. C++23 adds standard fixed-width floating point types in `<stdfloat>`.

## 1. Legacy Way (C++11 / C++17)
Standard `float` and `double`.

```cpp
#include <iostream>
#include <iomanip>

int main() {
    float f = 3.14f;
    double d = 3.1415926535;

    std::cout << std::fixed << std::setprecision(2) << f << "\n"; // Output: 3.14
    return 0;
}
```

## 2. Modern Way (C23)
Using C++23 `<stdfloat>` for guaranteed precision.

```cpp
#include <iostream>
#include <stdfloat> // C++23

int main() {
    std::float32_t f = 3.14f;
    std::float64_t d = 3.1415926535;

    // Hexadecimal float literals
    auto hex_f = 0x1.p+3; // 8.0

    std::cout << (double)hex_f << "\n"; // Output: 8.000000
    return 0;
}
```

# The Logic Bridge
// Logic: C++23 fixed-width floats solve the same portability problem that `stdint.h` solved for integers, ensuring exactly 32 or 64 bits of precision regardless of the platform.
