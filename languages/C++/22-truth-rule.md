# 🟢 Standard: Truth Rule [CORE]

## Definition
C++ truthiness is based on zero-parity (0 is false, non-zero is true) but adds the native `bool` type and `std::boolalpha` for literal printing.

## 1. Legacy Way (C++11 / C++17)
Standard logic evaluation.

```cpp
#include <iostream>

int main() {
    int x = 10;
    bool is_true = (x != 0);

    if (x) {
        std::cout << "X is True\n"; // Output: X is True
    }

    std::cout << std::boolalpha << is_true << "\n"; // Output: true
    return 0;
}
```

## 2. Modern Way (C23)
Identical logic, mirroring same tasks with modern attributes.

```cpp
#include <iostream>

int main() {
    auto x = 10;
    bool is_true = (x != 0);

    if (x) {
        std::cout << "X is True\n"; // Output: X is True
    }

    std::cout << std::boolalpha << is_true << "\n"; // Output: true
    return 0;
}
```

# The Logic Bridge
// Logic: Non-zero values are implicitly cast to `true` when used in a conditional context. This is handled at the CPU level by checking the Zero Flag.
