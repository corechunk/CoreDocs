# 🟢 Standard: Definite Iteration (For) [CORE]

## Definition
Standard counting loops and **Range-Based For** (C++11) for iterating over collections.

## 1. Legacy Way (C++11 / C++17)
Standard counting loop.

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> v = {1, 2, 3};
    for (int i = 0; i < v.size(); i++) {
        std::cout << v[i] << " ";
    }
    // Output: 1 2 3
    return 0;
}
```

## 2. Modern Way (C23)
Using Range-based for and C++20 `std::views`.

```cpp
#include <iostream>
#include <vector>
#include <ranges> // C++20

int main() {
    std::vector<int> v = {1, 2, 3};
    
    // Range-based for (Modern standard)
    for (const auto& i : v) {
        std::cout << i << " ";
    }
    // Output: 1 2 3
    return 0;
}
```

# The Logic Bridge
// Logic: A range-based for loop is transformed by the compiler into a standard loop using iterators (`v.begin()` to `v.end()`), hiding the complexity of pointer traversal.
