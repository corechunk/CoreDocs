# 🟢 Standard: Variables & Constants [CORE]

## Definition
Variables are mutable storage; constants are immutable. Modern C++ emphasizes compile-time constant evaluation (`constexpr`) for better performance and safety.

## 1. Legacy Way (C++11 / C++17)
Using `const` and basic initialization.

```cpp
#include <iostream>

#define MAX_VAL 100 // C-style macro

int main() {
    const int limit = 50; // Read-only variable
    int score = 0;        // Mutable variable
    
    std::cout << "Max: " << MAX_VAL << "\n"; // Output: Max: 100
    std::cout << "Limit: " << limit << "\n"; // Output: Limit: 50
    return 0;
}
```

## 2. Modern Way (C23)
Targeting C++23 native `constexpr` and `consteval` for true compile-time logic.

```cpp
#include <iostream>

int main() {
    // constexpr: Native keyword. Compile-time constant.
    constexpr int MAX_VAL = 100;
    
    // C++23 allows auto for constexpr
    constexpr auto limit = 50;
    int score = 0;

    std::cout << "Max: " << MAX_VAL << "\n"; // Output: Max: 100
    std::cout << "Limit: " << limit << "\n"; // Output: Limit: 50
    return 0;
}
```

# The Logic Bridge
// Logic: While `const` is checked at runtime (read-only memory), `constexpr` is evaluated by the compiler, allowing the value to be used in contexts like array sizes or template parameters.
