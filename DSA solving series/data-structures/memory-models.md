# 🧠 Systems & Memory Models

## 1. The Objective
Understanding how data is physically stored in memory is the difference between "code that works" and "high-performance engineering". This topic covers the layout of the Stack and Heap, and why data arrangement (Contiguity) impacts CPU speed.

---

## 2. Visual Logic
### Stack vs. Heap Layout
```text
[ STACK ] -> Grows Down (Fast, Auto-managed, Small)
    |  (Local variables, Function calls)
    V
[ FREE SPACE / RAM ]
    ^
    |  (Dynamic objects, Large data sets)
[ HEAP  ] -> Grows Up (Slower, Manual/Smart-ptr, Large)
```

### Cache Locality
- **Contiguous (Array):** `[A][B][C][D]` -> CPU loads all at once. Fast.
- **Linked (Node):** `[A]->...ptr...->[B]` -> CPU jumps around RAM. Slow (Cache Misses).

---

## 3. The Logic Bridge
- **Spatial Locality:** Modern CPUs don't just fetch one byte; they fetch a "Cache Line" (usually 64 bytes). If your data is in an array, the next items are already in the CPU cache. If you use linked nodes, the CPU wastes time waiting for RAM fetches.
- **Lifetime Management:** Stack memory is reclaimed the moment a function returns. Heap memory persists until you `delete` it or the `unique_ptr` goes out of scope.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Memory Comparison)

```cpp
#include <iostream>
#include <vector>

struct Point {
    int x, y;
};

int main() {
    // 1. STACK ALLOCATION (Fastest)
    Point p1 = {10, 20}; 

    // 2. HEAP ALLOCATION (Flexible but requires cleanup)
    Point* p2 = new Point{30, 40};

    // 3. CONTIGUOUS HEAP (Best for performance)
    std::vector<Point> points;
    points.push_back({1, 2});
    points.push_back({3, 4});

    std::cout << "Stack Point: " << p1.x << ", " << p1.y << std::endl;
    std::cout << "Heap Point: " << p2->x << ", " << p2->y << std::endl;

    delete p2; // Manual cleanup
    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
