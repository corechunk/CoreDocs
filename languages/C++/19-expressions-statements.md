# 🟢 Standard: Expressions & Statements [CORE]

## Definition
Expressions reduce to a value; Statements are instructions. C++23 adds more context for expression categories (lvalues vs rvalues).

## 1. Legacy Way (C++11 / C++17)
Basic expression evaluation.

```cpp
#include <iostream>

int main() {
    int x = 5 + 5; // x = 10 is a statement
    std::cout << x << "\n"; // Output: 10
    return 0;
}
```

## 2. Modern Way (C23)
Using `auto` and modern attributes.

```cpp
#include <iostream>

int main() {
    auto x = 5 + 5; 
    std::cout << x << "\n"; // Output: 10
    return 0;
}
```

# The Logic Bridge
// Logic: Expressions produce temporary values (rvalues) which can be moved into permanent memory (lvalues). C++ uses these categories to optimize memory copying.
