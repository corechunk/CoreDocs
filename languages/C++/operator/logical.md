# 🟢 Standard: Logical Operators [CORE]

## Definition
Boolean logic symbols: `&&` (AND), `||` (OR), and `!` (NOT).

## 1. Legacy Way (C++11 / C++17)
Standard usage with `std::boolalpha`.

```cpp
#include <iostream>

int main() {
    bool a = true, b = false;
    std::cout << std::boolalpha << (a && b) << "\n"; // Output: false
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring same task with `auto`.

```cpp
#include <iostream>

int main() {
    auto a = true, b = false;
    std::cout << std::boolalpha << (a && b) << "\n"; // Output: false
    return 0;
}
```

# The Logic Bridge
// Logic: C++ uses short-circuiting. For `a || b`, if `a` is true, `b` is never evaluated, which is essential for performance and safety (e.g., checking for null before dereferencing).
