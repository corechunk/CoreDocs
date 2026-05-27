# 🟢 Standard: Recursion [CORE]

## Definition
Functions calling themselves. C++ compilers often optimize **Tail Recursion** into a simple loop (Tail Call Optimization - TCO).

## 1. Legacy Way (C++11 / C++17)
Standard recursive factorial.

```cpp
#include <iostream>

long long fact(int n) {
    if (n <= 1) return 1;
    return n * fact(n - 1);
}

int main() {
    std::cout << fact(5) << "\n"; // Output: 120
    return 0;
}
```

## 2. Modern Way (C23)
Using `constexpr` recursion for compile-time calculation.

```cpp
#include <iostream>

// constexpr: Calculated during compilation if possible
constexpr long long fact(int n) {
    if (n <= 1) return 1;
    return n * fact(n - 1);
}

int main() {
    // Computed at compile-time
    constexpr auto res = fact(5);
    std::cout << res << "\n"; // Output: 120
    return 0;
}
```

# The Logic Bridge
// Logic: Each recursion depth uses a Stack frame. `constexpr` recursion shifts this cost from the user's CPU at runtime to the developer's CPU at build-time.
