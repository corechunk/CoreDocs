# 🔴 Standard: Dynamic Arrays (Vector) [SYSTEMS]

## Definition
`std::vector` is the default dynamic collection. It handles reallocation and growth automatically.

## 1. Legacy Way (C++11 / C++17)
Manual capacity management.

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> v;
    v.reserve(10); // Optimization
    v.push_back(1);
    
    std::cout << "Cap: " << v.capacity() << "\n"; // Output: Cap: 10
    return 0;
}
```

## 2. Modern Way (C23)
Using `std::vector` with C++23 features like `std::ranges`.

```cpp
#include <iostream>
#include <vector>
#include <ranges>

int main() {
    auto v = std::vector{3, 1, 2};
    std::ranges::sort(v); // Modern sorting
    
    for (auto i : v) std::cout << i << " "; // Output: 1 2 3
    return 0;
}
```

# The Logic Bridge
// Logic: Vectors use an "Exponential Growth" strategy (usually doubling capacity) to ensure that the average (amortized) cost of adding an element is O(1).
