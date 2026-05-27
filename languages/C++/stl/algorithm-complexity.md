# 📊 STL Algorithm Complexity

## 1. The Objective
Every STL algorithm comes with a **Complexity Guarantee** mandated by the C++ Standard. Understanding these guarantees is crucial for writing high-performance code that doesn't slow down as data grows.

---

## 2. Visual Logic
### The Big O Table
| Algorithm | Complexity | Why? |
| :--- | :--- | :--- |
| `std::find` | $O(n)$ | Linear scan. |
| `std::sort` | $O(n \log n)$ | Introsort (Quick + Heap). |
| `std::binary_search` | $O(\log n)$ | Halving space (requires Random Access). |
| `std::accumulate` | $O(n)$ | Single pass summation. |

---

## 3. The Logic Bridge
- **Iterator Impact:** An algorithm's speed depends on the **Iterator Category** provided. `std::distance` is $O(1)$ for a vector (pointer math) but $O(n)$ for a list (counting nodes).
- **The "N" Guarantee:** Algorithms like `std::nth_element` provide $O(n)$ average time to find the $K$-th largest item, which is significantly faster than sorting the entire collection ($O(n \log n)$).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Speed Test)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <chrono>

int main() {
    std::vector<int> v(1000000, 1);
    
    auto start = std::chrono::high_resolution_clock::now();
    
    // O(n) operation
    auto count = std::count(v.begin(), v.end(), 1);

    auto end = std::chrono::high_resolution_clock::now();
    std::chrono::duration<double> diff = end - start;
    
    std::cout << "O(n) scan took: " << diff.count() << "s\n";
    return 0;
}
```

---
[➔ Back to Algorithm Hub](04-algorithms.md)
