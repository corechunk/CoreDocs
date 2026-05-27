# 🧱 STL Array (Fixed-Size)

## 1. The Objective
`std::array` is a thin wrapper around a standard C-style array. It provides the performance of a raw array but with the benefits of a standard container (like `size()`, `at()`, and Iterator support).

---

## 2. Visual Logic
### Fixed Allocation (Stack)
```text
Array: [ A | B | C | D | E ]
Size:  5 (Fixed at compile-time)
```
- No heap allocation. Data lives directly on the stack.

---

## 3. The Logic Bridge
- **Zero Overhead:** Unlike `vector`, `std::array` has zero memory overhead. It doesn't store capacity or pointers to the heap.
- **Safety:** Using `.at(i)` instead of `[i]` provides bounds checking, throwing an exception if you go out of range.
- **When to Use:** Use whenever the size of the collection is known at compile-time and will never change. It is safer and more modern than raw `int arr[5]`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Full Usage)

```cpp
#include <iostream>
#include <array>
#include <algorithm>

int main() {
    // 1. Initialization
    std::array<int, 5> data = {5, 2, 8, 1, 9};

    // 2. Safe Access
    try {
        std::cout << data.at(2) << std::endl;
    } catch (const std::out_of_range& e) {
        std::cerr << "Error: " << e.what() << std::endl;
    }

    // 3. Algorithm Compatibility
    std::sort(data.begin(), data.end());

    // 4. Modern Loop
    for (const auto& x : data) std::cout << x << " ";

    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
