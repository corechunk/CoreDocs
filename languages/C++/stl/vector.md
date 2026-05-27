# 📈 STL Vector (Dynamic Array) - Master Reference

## 1. The Objective
`std::vector` is a sequence container that encapsulates dynamic size arrays. Elements are stored contiguously, allowing $O(1)$ random access and efficient iteration.

---

## 2. Visual Logic
### Memory Growth
```text
Capacity: 4 | [ A | B | C | D ]
push_back(E) -> Reallocate (Capacity 8)
[ A | B | C | D | E | _ | _ | _ ]
```

---

## 3. # The Logic Bridge (Key Points)

- **Iterator Invalidation:** 
  - `push_back`/`insert`: Invalidates ALL if `new_size > capacity`. Invalidates from point of change if no reallocation.
  - `pop_back`/`erase`: Invalidates from point of change to `end()`.
- **Exception Safety:** Provides the **Strong Guarantee** (rollback on failure) if elements have a `noexcept` move constructor.
- **Data Access:** `&v[0]` or `v.data()` is guaranteed to be a raw pointer to the underlying contiguous C-array.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int main() {
    // --- 1. CONSTRUCTORS ---
    std::vector<int> v_empty;
    std::vector<int> v_size(5, 100);       // {100, 100, 100, 100, 100}
    std::vector<int> v_range(v_size.begin(), v_size.begin() + 2); // {100, 100}
    std::vector<int> v_list = {1, 2, 3};   // Initializer list

    // --- 2. ELEMENT ACCESS ---
    int val = v_list[1];                   // Fast but unsafe
    int safe_val = v_list.at(1);           // Throws out_of_range if invalid
    int& head = v_list.front();            // Reference to first
    int& tail = v_list.back();             // Reference to last
    int* ptr = v_list.data();              // Raw pointer to array

    // --- 3. ITERATORS ---
    auto it = v_list.begin();              // Forward
    auto rit = v_list.rbegin();            // Reverse
    auto cit = v_list.cbegin();            // Const (read-only)

    // --- 4. CAPACITY ---
    bool empty = v_list.empty();
    size_t size = v_list.size();
    v_list.reserve(100);                   // Change capacity, not size
    v_list.shrink_to_fit();                // Request removal of unused capacity

    // --- 5. MODIFIERS ---
    v_list.push_back(4);                   // Add to end
    v_list.emplace_back(5);                // Construct in-place (Efficient)
    v_list.pop_back();                     // Remove from end
    
    v_list.insert(v_list.begin() + 1, 99); // {1, 99, 2, 3, 4}
    v_list.emplace(v_list.begin() + 1, 88);// {1, 88, 99, 2, 3, 4}
    
    v_list.erase(v_list.begin() + 1);      // Remove 88
    v_list.clear();                        // Remove everything (size=0)
    v_list.resize(10, 0);                  // Change size to 10, fill with 0

    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
