# 🟢 Standard: Associative Collections [CORE]

## Definition
C++ provides `std::map` (Balanced Tree, Ordered) and `std::unordered_map` (Hash Table, Unordered) for Key-Value associations.

## 1. Legacy Way (C++11 / C++17)
Standard map usage.

```cpp
#include <iostream>
#include <map>
#include <string>

int main() {
    std::map<std::string, int> scores;
    scores["Neo"] = 100;
    
    std::cout << "Score: " << scores["Neo"] << "\n"; // Output: Score: 100
    return 0;
}
```

## 2. Modern Way (C23)
Using **Structured Bindings** (C++17) and C++23 `contains()`.

```cpp
#include <iostream>
#include <unordered_map>
#include <string>

int main() {
    auto scores = std::unordered_map<std::string, int>{ {"Neo", 100} };

    if (scores.contains("Neo")) { // C++20/23
        for (const auto& [name, val] : scores) { // Structured Bindings
            std::cout << name << ": " << val << "\n"; // Output: Neo: 100
        }
    }
    return 0;
}
```

# The Logic Bridge
// Logic: `std::map` uses a Red-Black Tree (O(log N)). `std::unordered_map` uses a Hash Table (O(1) average), trading memory for speed and losing element ordering.
