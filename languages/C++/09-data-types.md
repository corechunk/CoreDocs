# 🟢 Standard: Data Types [CORE]

## Definition
Types define how bytes are interpreted. C++ is a strongly-typed language that has moved from C-style primitives to native Boolean types and type deduction.

## 1. Legacy Way (C++11 / C++17)
Standard primitives and the requirement of headers for fixed-width types.

```cpp
#include <iostream>
#include <cstdint> // Required for int32_t, etc.

int main() {
    int i = 10;
    float f = 3.14f;
    double d = 3.14159;
    char c = 'A';
    bool b = true; // Native in C++ since C++98
    const char* s = "Hello";

    std::cout << "Int: " << i << "\n";   // Output: Int: 10
    std::cout << "Bool: " << b << "\n";  // Output: Bool: 1
    return 0;
}
```

## 2. Modern Way (C23)
Using `auto` for type deduction and modern literals.

```cpp
#include <iostream>
#include <cstdint>

int main() {
    auto i = 10;      // Deducts int
    auto f = 3.14f;   // Deducts float
    auto b = true;    // Deducts bool
    auto s = "Hello"; // Deducts const char*

    std::cout << "Int: " << i << "\n";   // Output: Int: 10
    std::cout << "Bool: " << b << "\n";  // Output: Bool: 1
    return 0;
}
```

## Deep-Dive Reference
For exhaustive width variants and memory layouts:
- [Integers](./data-type/integers.md) | [Floating Point](./data-type/floats.md) | [Fixed-Width](./data-type/fixed-width.md) | [Special Types](./data-type/special-types.md)

# The Logic Bridge
// Logic: C++ type deduction (`auto`) happens at compile-time. The binary produced is identical to explicit typing, but the source code is cleaner and more maintainable.
