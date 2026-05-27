# ⚙️ STL Algorithm Engine

## 1. The Objective
The Algorithms library provides functions for range-based tasks (Sorting, Searching, Modifying, Counting). These are "Generic" because they work on any container via iterators.

---

## 2. Visual Logic
### The Pipeline
`[ Container ] -> [ Iterator Range ] -> [ Algorithm ] -> [ Result ]`

---

## 3. The Logic Bridge
- **Decoupling:** Algorithms don't know about containers; they only know about iterators. This is why you can use the same `std::sort` on an Array or a Vector.
- **Performance:** STL algorithms are often more optimized than hand-written loops (using loop unrolling and special CPU instructions).
- **Ranges (C++20):** `std::ranges::sort(v)` is now the standard over `std::sort(v.begin(), v.end())`.

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

    // 3. Count
    int counts = std::count(v.begin(), v.end(), 8);

    std::cout << "Sum: " << sum << ", Counts of 8: " << counts << std::endl;
    return 0;
}
```

---
[➔ Back to STL Hub](00-stl-overview.md)
