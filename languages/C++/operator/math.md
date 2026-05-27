# 🟢 Standard: Mathematical Operators [CORE]

## Definition
Symbols for arithmetic. C++ supports standard operators and advanced math via `<cmath>`.

## 1. Legacy Way (C++11 / C++17)
Standard `+`, `-`, `*`, `/`, `%`.

```cpp
#include <iostream>

int main() {
    int x = 10, y = 3;
    std::cout << "Div: " << (x / y) << "\n"; // Output: Div: 3
    std::cout << "Mod: " << (x % y) << "\n"; // Output: Mod: 1
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring arithmetic using `auto` and modern literals.

```cpp
#include <iostream>

int main() {
    auto x = 10, y = 3;
    std::cout << "Div: " << (x / y) << "\n"; // Output: Div: 3
    std::cout << "Mod: " << (x % y) << "\n"; // Output: Mod: 1
    return 0;
}
```

# The Logic Bridge
// Logic: Floating point division returns a decimal, while integer division truncates the remainder toward zero.
