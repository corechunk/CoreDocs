# 🧱 STL Array (Fixed-Size) - Master Reference

## 1. The Objective
`std::array` is a container that encapsulates fixed-size arrays. It is a very thin wrapper that provides standard container methods without sacrificing the performance of C-style arrays.

---

## 2. Visual Logic
### Stack Allocation
```text
Memory [ Stack ]
| ... |
| [ 10 | 20 | 30 ] | <-- std::array<int, 3> lives here
| ... |
```

---

## 3. # The Logic Bridge (Key Points)

- **Zero Overhead:** An `std::array<int, 5>` is exactly the same size in memory as `int[5]`.
- **Pass-by-Value:** Unlike raw arrays, `std::array` can be passed by value to functions (it copies the entire contents) and can be assigned to another array of the same type/size.
- **Safety:** Always use `.at()` for bounds-checked access to prevent buffer overflow vulnerabilities.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <array>
#include <algorithm>

int main() {
    // --- 1. INITIALIZATION ---
    std::array<int, 5> a1 = {1, 2, 3, 4, 5};
    std::array<int, 5> a2;
    a2.fill(10);                           // Set all to 10

    // --- 2. ACCESS ---
    int x = a1[0];
    int y = a1.at(1);                      // Throws if out of bounds
    int f = a1.front();
    int b = a1.back();
    int* p = a1.data();                    // Pointer to internal raw array

    // --- 3. SIZE ---
    constexpr size_t s = a1.size();        // Known at compile time
    bool empty = a1.empty();

    // --- 4. COMPARISON ---
    if (a1 == a2) std::cout << "Equal\n";  // Works as expected

    // --- 5. ITERATION ---
    for(auto it = a1.rbegin(); it != a1.rend(); ++it) {
        std::cout << *it << " ";
    }

    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
