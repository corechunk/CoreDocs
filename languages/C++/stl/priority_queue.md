# 🔝 STL Priority Queue - Master Reference

## 1. The Objective
`std::priority_queue` is a container adapter that provides constant-time lookup of the largest element. It is essentially an implementation of a **Binary Heap**.

---

## 2. Visual Logic
### Priority Ordering
```text
Items: [ 10, 50, 30 ]
pq.top() -> 50 (Always highest)
```

---

## 3. # The Logic Bridge (Key Points)

- **Complexity:** `push` and `pop` are **$O(\log n)$**. `top` is **$O(1)$**.
- **No `at()` or `operator[]`:** You can only interact with the `top` element.
- **Min-Heap Trick:** By default it's a Max-Heap. Use `std::greater<T>` to make it a Min-Heap.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <queue>
#include <vector>
#include <functional>

int main() {
    // --- 1. INITIALIZATION (Max-Heap) ---
    std::priority_queue<int> max_pq;

    // --- 2. INITIALIZATION (Min-Heap) ---
    std::priority_queue<int, std::vector<int>, std::greater<int>> min_pq;

    // --- 3. MODIFIERS ---
    max_pq.push(10);
    max_pq.push(50);
    max_pq.emplace(30);

    // --- 4. ACCESS & REMOVAL ---
    while (!max_pq.empty()) {
        std::cout << max_pq.top() << " ";  // Output: 50 30 10
        max_pq.pop();
    }

    // --- 5. SIZE ---
    std::cout << "\nRemaining: " << max_pq.size() << "\n";

    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
