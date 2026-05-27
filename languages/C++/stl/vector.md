# 📈 STL Vector (Dynamic Array)

## 1. The Objective
`std::vector` is the go-to sequential container in C++. It is a dynamic array that manages its own memory, growing automatically as elements are added. It provides $O(1)$ random access and amortized $O(1)$ insertion at the end.

---

## 2. Visual Logic
### Internal Layout
```text
[ Data: Pointer to Heap Array ]
[ Size: Current number of elements ]
[ Capacity: Total space allocated ]

Array in Heap: [ A | B | C | D | _ | _ | _ | _ ]
                 ^           ^               ^
                Size: 4    Capacity: 8
```

---

## 3. The Logic Bridge
- **Cache Efficiency:** Because data is contiguous, vectors are the fastest container for iteration.
- **Iterator Invalidation:** Adding elements can trigger a "Reallocation" (moving to a new, larger array). When this happens, all previous pointers/iterators to elements in the vector become **Invalid** (dangling pointers).
- **Modern Optimization:** Modern compilers use **Move Semantics** to make resizing extremely fast, making `vector` superior to `list` for almost all use cases under 100,000 elements.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Full Usage)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    // 1. Initialization (C++17 CTAD)
    std::vector v = {10, 20, 30, 40};

    // 2. Efficient Addition
    v.reserve(10); // Prevent frequent reallocations
    v.push_back(50);
    v.emplace_back(60); // Construct in-place (more efficient)

    // 3. Modern Iteration (C++20)
    for (const auto& x : v) std::cout << x << " ";
    
    // 4. Capacity vs Size
    std::cout << "\nSize: " << v.size() << ", Cap: " << v.capacity();

    // 5. Shrink to Fit (Reclaiming memory)
    v.shrink_to_fit();

    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
