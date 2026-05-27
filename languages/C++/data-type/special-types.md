# 🔴 Standard: Special Purpose Types [SYSTEMS]

## Definition
Types for memory management and meta-programming, including `std::nullptr_t`, `size_t`, and `void`.

## 1. Legacy Way (C++11 / C++17)
Using `nullptr` and `size_t`.

```cpp
#include <iostream>
#include <cstddef>

int main() {
    void* ptr = nullptr;
    size_t s = sizeof(int);

    if (ptr == nullptr) {
        std::cout << "Empty\n"; // Output: Empty
    }
    return 0;
}
```

## 2. Modern Way (C23)
Using modern attributes and native type-inference.

```cpp
#include <iostream>

int main() {
    auto ptr = nullptr; // Deducts std::nullptr_t
    auto s = sizeof(int);

    if (ptr == nullptr) {
        std::cout << "Empty\n"; // Output: Empty
    }
    return 0;
}
```

# The Logic Bridge
// Logic: `size_t` is guaranteed to be large enough to contain the size of the largest possible object in memory. It is the return type of the `sizeof` operator.
