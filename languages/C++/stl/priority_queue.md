# 🔝 STL Priority Queue (Adapter)

## 1. The Objective
`std::priority_queue` is a container adapter that provides constant-time access to the **largest** (or smallest) element. It behaves like a Queue where elements are ordered by priority rather than arrival time.

---

## 2. Visual Logic
### The Binary Heap Wrapper
Internally, it uses `std::vector` and the `std::make_heap` algorithms to maintain a **Max-Heap** property.
```text
          [ 100 ]  <-- Always at the top
         /       \
      [ 50 ]    [ 80 ]
```

---

## 3. # The Logic Bridge (Key Points)

- **Default Behavior:** It is a **Max-Heap** by default (highest value on top).
- **Custom Ordering:** To make it a **Min-Heap**, you must provide a comparator: `std::priority_queue<int, std::vector<int>, std::greater<int>>`.
- **Complexity:** `top()` is $O(1)$, but `push()` and `pop()` are **$O(\log n)$** because they must restore the heap property.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Full Usage)

```cpp
#include <iostream>
#include <queue>
#include <vector>

int main() {
    // 1. Max-Heap (Default)
    std::priority_queue<int> pq;
    pq.push(10);
    pq.push(30);
    pq.push(20);

    std::cout << "Max-Heap Top: " << pq.top() << "\n"; // 30

    // 2. Min-Heap (Custom)
    std::priority_queue<int, std::vector<int>, std::greater<int>> min_pq;
    min_pq.push(10);
    min_pq.push(30);
    min_pq.push(20);

    std::cout << "Min-Heap Top: " << min_pq.top() << "\n"; // 10

    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
