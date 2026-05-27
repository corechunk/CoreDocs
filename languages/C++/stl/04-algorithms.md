# ⚙️ STL Algorithm Engine

## 1. The Objective
The Algorithms library provides functions for range-based tasks (Sorting, Searching, Modifying, Counting). These are "Generic" because they work on any container via iterators.

---

## 2. Visual Logic
### The Pipeline
`[ Container ] -> [ Iterator Range ] -> [ Algorithm ] -> [ Result ]`

---

## 3. # The Logic Bridge (Key Points)

### Classification
- **Non-Modifying:** `find`, `count`, `all_of`, `search`.
- **Modifying:** `copy`, `move`, `transform`, `replace`.
- **Sorting:** `sort`, `stable_sort`, `partial_sort`, `nth_element`.
- **Numeric:** `accumulate`, `iota`, `inner_product`.

### The Range Advantage
Modern C++ (C++20) introduces the `std::ranges` namespace. This allows passing the container itself instead of iterator pairs.
```cpp
std::ranges::sort(v); // Instead of std::sort(v.begin(), v.end())
```

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Common Algos)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <numeric>

int main() {
    std::vector v = {5, 2, 8, 1, 9};

    // 1. Sort
    std::sort(v.begin(), v.end());

    // 2. Accumulate (Sum)
    int sum = std::accumulate(v.begin(), v.end(), 0);

    std::cout << "Sum: " << sum << std::endl;
    return 0;
}
```

---

## 🔗 Granular Sub-Topics
- [Algorithm Complexity](algorithm-complexity.md) - Performance guarantees.
- [Stable vs. Unstable](stable-vs-unstable.md) - Preserving relative order.

[➔ Back to STL Hub](00-stl-overview.md)
