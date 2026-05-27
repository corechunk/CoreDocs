# 🔴 Standard: Fixed-Width Types [SYSTEMS]

## Definition
Fixed-width types guarantee bit-counts. In C++, these are found in `<cstdint>`.

## 1. Legacy Way (C++11 / C++17)
Standard usage of `int32_t` and `uint64_t`.

```cpp
#include <iostream>
#include <cstdint>

int main() {
    int8_t  a = 127;
    uint32_t b = 0xFFFFFFFF;

    std::cout << (int)a << "\n"; // Output: 127
    return 0;
}
```

## 2. Modern Way (C23)
Using modern literals and bit-precise types if supported.

```cpp
#include <iostream>
#include <cstdint>

int main() {
    uint64_t huge = 0xFFFF_FFFF_FFFF_FFFF; // Separators
    uint8_t mask = 0b1010_1010;

    std::cout << (int)mask << "\n"; // Output: 170
    return 0;
}
```

# The Logic Bridge
// Logic: `<cstdint>` types are aliases. On most systems, `int32_t` is an alias for `int`, but on some specialized hardware, it might be an alias for `long`.
