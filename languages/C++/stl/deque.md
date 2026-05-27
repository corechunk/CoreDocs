# ↔️ STL Deque (Double-Ended Queue) - Master Reference

## 1. The Objective
`std::deque` is an indexed sequence container that allows for fast insertion and deletion at both its beginning and its end. Unlike `vector`, it is not guaranteed to store all its elements in contiguous memory.

---

## 2. Visual Logic
### Segmented Architecture
```text
[ Block 1: A, B ] -> [ Block 2: C, D ] -> [ Block 3: E, F ]
       |                    |                    |
       \____________________|____________________/
                            |
                      [ Map of Pointers ]
```

---

## 3. # The Logic Bridge (Key Points)

- **End-Heavy Performance:** `push_front` and `pop_front` are $O(1)$, which is significantly faster than `vector` ($O(n)$).
- **Iterator Invalidation:** More complex than vector. Adding elements to the ends **does not** invalidate pointers to existing elements, but **may** invalidate all iterators.
- **No `reserve()`:** Deques do not have a capacity/reserve system like vectors because they allocate new blocks on demand.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <deque>
#include <algorithm>

int main() {
    // --- 1. CONSTRUCTORS ---
    std::deque<int> dq1 = {1, 2, 3};
    std::deque<int> dq2(5, 10);            // {10, 10, 10, 10, 10}

    // --- 2. ELEMENT ACCESS ---
    int first = dq1.front();
    int last = dq1.back();
    int val = dq1[1];
    int safe_val = dq1.at(1);

    // --- 3. MODIFIERS (Double-Ended) ---
    dq1.push_front(0);
    dq1.push_back(4);
    dq1.emplace_front(-1);
    dq1.emplace_back(5);

    dq1.pop_front();
    dq1.pop_back();

    // --- 4. MIDDLE OPS (O(n)) ---
    dq1.insert(dq1.begin() + 1, 99);
    dq1.erase(dq1.begin() + 1);

    // --- 5. CAPACITY & CLEANUP ---
    dq1.shrink_to_fit();
    dq1.clear();

    // --- 6. ITERATION ---
    for(const auto& x : dq2) std::cout << x << " ";

    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
