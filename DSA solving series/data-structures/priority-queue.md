# 🔝 Priority Queue

## 1. The Objective
A Priority Queue is an extension of a regular queue where each element has a **priority** associated with it. Elements are dequeued based on their priority (usually highest priority first), not just their arrival time.

---

## 2. Visual Logic
### Priority Ordering
```text
Task: [ Wash Dishes (P3) ]
Task: [ Call Hospital (P1) ]
Task: [ Pay Bills (P2) ]

Dequeue Order: Call Hospital -> Pay Bills -> Wash Dishes
```
- Internally, this is most efficiently implemented using a **Binary Heap**.

---

## 3. The "Aha!" Moment
- **Intelligent Sorting:** It's not a fully sorted list; it's a "partially ordered" structure that only guarantees the *top* element is the highest/lowest. This makes it much faster ($O(\log n)$) than keeping a sorted array ($O(n)$ insertion).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (STL Priority Queue)

```cpp
#include <iostream>
#include <queue>

int main() {
    // Max-Heap by default
    std::priority_queue<int> pq;

    pq.push(10);
    pq.push(30);
    pq.push(20);

    std::cout << "Highest Priority: " << pq.top() << std::endl; // 30

    pq.pop();
    std::cout << "Next Highest: " << pq.top() << std::endl; // 20

    return 0;
}
```

---
[➔ Back to Queue Hub](queue.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
