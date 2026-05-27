# 🟢 Standard: If/Else Logic [CORE]

## Definition
Standard decision making. Modern C++ allows for **Compile-time If** (`if constexpr`) to enable template branching.

## 1. Legacy Way (C++11 / C++17)
Standard runtime branching.

```cpp
#include <iostream>

int main() {
    int score = 85;
    if (score >= 90) std::cout << "A\n";
    else if (score >= 80) std::cout << "B\n"; // Output: B
    else std::cout << "F\n";
    return 0;
}
```

## 2. Modern Way (C23)
Using `if constexpr` (C++17) for compile-time decision making.

```cpp
#include <iostream>
#include <type_traits>

template <typename T>
void check_type(T val) {
    if constexpr (std::is_integral_v<T>) {
        std::cout << "Integer\n"; // Output: Integer
    } else {
        std::cout << "Other\n";
    }
}

int main() {
    check_type(10);
    return 0;
}
```

# The Logic Bridge
// Logic: Runtime `if` is evaluated every time the code runs. `if constexpr` is evaluated during compilation; the branch that is false is physically discarded from the binary.
