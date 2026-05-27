# 🔵 Standard: Standard Library (STL) [PRO]

## Definition
The C++ Standard Library (STL) provides containers, algorithms, and utilities. C++20/23 adds **Ranges** and **std::print**.

## 1. Legacy Way (C++11 / C++17)
Standard STL usage.

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    std::vector<int> v = {3, 1, 2};
    std::sort(v.begin(), v.end());
    
    for (auto i : v) std::cout << i << " "; // Output: 1 2 3
    return 0;
}
```

## 2. Modern Way (C23)
Using **Ranges** (C++20) for composable algorithms.

```cpp
#include <iostream>
#include <vector>
#include <ranges>
#include <algorithm>

int main() {
    std::vector<int> v = {3, 1, 2};
    std::ranges::sort(v); // Range-aware sort
    
    auto view = v | std::views::reverse; // Composable view
    
    for (auto i : view) std::cout << i << " "; // Output: 2 1 3
    return 0;
}
```

# The Logic Bridge
// Logic: The STL is a "Header-Only" library for templates and a pre-compiled binary for core types. Modern Ranges use "Lazy Evaluation," creating views that don't physically move data until iterated.
