# 🟢 Standard: Order of Operations [CORE]

## Definition
Precedence (which operator first) and Associativity (direction).

## 1. Legacy Way (C++11 / C++17)
Standard rules.

```cpp
#include <iostream>

int main() {
    int res = 5 + 10 * 2;
    std::cout << res << "\n"; // Output: 25
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring same math task.

```cpp
#include <iostream>

int main() {
    auto res = 5 + 10 * 2;
    std::cout << res << "\n"; // Output: 25
    return 0;
}
```

# The Logic Bridge
// Logic: Precedence is a syntactic rule. The compiler's parser uses these rules to structure the execution tree so that multiplicative nodes are evaluated before additive nodes.
