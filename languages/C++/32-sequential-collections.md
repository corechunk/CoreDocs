# 🟢 Standard: Sequential Collections [CORE]

## Definition
Sequential collections in C++ include stack-allocated `std::array` and heap-allocated `std::vector`. Unlike raw C arrays, these provide size safety and STL iterator support.

## 1. Legacy Way (C++11)
Standard `std::vector` usage.

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> v = {10, 20, 30};
    v.push_back(40);
    
    std::cout << "Size: " << v.size() << "\n"; // Output: Size: 4
    return 0;
}
```

## 2. Modern Way (C23)
Using `std::vector` with C++23 `contains` (for set-like checks) and modern initializers.

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    auto v = std::vector{10, 20, 30}; // CTAD (C++17)
    v.push_back(40);

    // C++23 range-based search
    if (std::ranges::find(v, 20) != v.end()) {
        std::cout << "Found 20\n"; // Output: Found 20
    }
    return 0;
}
```

## Deep-Dive Reference
For memory layouts and dimensional grids:
- [Fixed-Size (std::array)](./array/fixed.md) | [Dynamic (std::vector)](./array/vla.md) | [Multi-Dimensional](./array/multidim.md)

# The Logic Bridge
// Logic: `std::vector` manages a heap-allocated array. When capacity is exceeded, it allocates a new, larger block, moves the elements (using Move Semantics), and deletes the old block.
