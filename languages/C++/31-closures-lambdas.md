# 🔵 Standard: Closures & Lambdas [PRO]

## Definition
**Lambdas** are anonymous functions that can "Capture" variables from their surrounding scope (Closures). Standardized in C++11.

## 1. Legacy Way (C++11 / C++17)
Basic lambda with value capture.

```cpp
#include <iostream>

int main() {
    int factor = 2;
    // [=] means capture everything by value
    auto multiply = [=](int x) { return x * factor; };

    std::cout << multiply(5) << "\n"; // Output: 10
    return 0;
}
```

## 2. Modern Way (C23)
Using generic lambdas and `constexpr` lambdas (C++17/20).

```cpp
#include <iostream>

int main() {
    // Generic Lambda (C++14)
    auto add = [](auto a, auto b) { return a + b; };
    
    // constexpr Lambda (C++17)
    constexpr auto res = [](int x) { return x * x; }(5);

    std::cout << add(5, 5) << " " << res << "\n"; // Output: 10 25
    return 0;
}
```

# The Logic Bridge
// Logic: A lambda is transformed by the compiler into a "Functor"—a unique, unnamed struct with an overloaded `operator()`. Captured variables become member variables of this struct.
