# 🟢 Standard: Keywords & Standards [CORE]

## Definition
Keywords are reserved words in C++. Standards (C++98 through C++23) define how the language vocabulary grows.

## 1. Legacy Way (C++98 / C++11)
Core vocabulary and the introduction of `auto` and `nullptr` in C++11.

```cpp
#include <iostream>

int main() {
    int* ptr = NULL; // Legacy C macro
    ptr = nullptr;   // C++11 Keyword
    
    std::cout << (ptr == nullptr) << "\n"; // Output: 1
    return 0;
}
```

## 2. Modern Way (C++23)
Expanding into native Boolean types, `constexpr`, and new reflection/module keywords.

```cpp
#include <iostream>

int main() {
    constexpr int x = 10; // C++11/20/23 Keyword
    bool active = true;   // Native keyword
    
    std::cout << "Active: " << active << "\n"; // Output: Active: 1
    return 0;
}
```

# The Logic Bridge
// Logic: Keywords are hard-coded into the compiler's symbol table. Standard updates (like C++23) add keywords that simplify code or enable better optimization (like `constexpr`).
