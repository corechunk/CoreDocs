# 📈 STL Vector (Dynamic Array) - Full Usage

## 1. The Objective
`std::vector` is the most versatile and efficient sequential container. It provides $O(1)$ random access and amortized $O(1)$ tail operations. It should be the default container for almost every use case.

---

## 2. Visual Logic
### Capacity vs. Size
```text
[ A | B | C | D | _ | _ | _ | _ ]
 <---- Size ---->
 <----------- Capacity --------->
```
- **Size:** Number of actual elements.
- **Capacity:** Reserved space to avoid frequent reallocations.

---

## 3. # The Logic Bridge (Key Points)

- **Perfect Forwarding (`emplace_back`):** Unlike `push_back`, which copies or moves an existing object, `emplace_back` constructs the object **directly inside** the vector's memory, saving a constructor call.
- **Iterator Invalidation:**
    - **Reallocation:** If `size > capacity`, all iterators are invalidated.
    - **No Reallocation:** If no resize happens, only iterators after the point of insertion/deletion are invalidated.
- **Exception Safety:** `vector` provides the **Strong Guarantee** (commit-or-rollback) if the element's move constructor is marked `noexcept`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (The Complete API)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    // --- 1. INITIALIZATION ---
    std::vector<int> v1;                     // Empty
    std::vector<int> v2(5, 100);             // {100, 100, 100, 100, 100}
    std::vector<int> v3 = {1, 2, 3, 4, 5};   // Initializer list

    // --- 2. ACCESS ---
    int first = v3.front();
    int last = v3.back();
    int second = v3.at(1); // Safe access (bounds checked)

    // --- 3. MODIFIERS ---
    v3.push_back(6);
    v3.emplace_back(7); // Construct in-place
    
    v3.insert(v3.begin() + 2, 99); // {1, 2, 99, 3, 4, 5, 6, 7}
    v3.erase(v3.begin() + 2);      // Remove 99
    
    // --- 4. CAPACITY MANAGEMENT ---
    v3.reserve(100);       // Pre-allocate space
    v3.shrink_to_fit();    // Reclaim unused capacity
    v3.clear();            // Remove all elements (size becomes 0)

    // --- 5. MODERN ITERATION ---
    for (int x : v2) std::cout << x << " ";

    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
