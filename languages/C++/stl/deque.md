# ↔️ STL Deque (Double-Ended Queue)

## 1. The Objective
`std::deque` (Double-Ended Queue) is a complex container that combines the benefits of `vector` and `list`. It provides $O(1)$ random access AND $O(1)$ insertion/deletion at **both** ends.

---

## 2. Visual Logic
### The "Map of Blocks"
Unlike `vector` (one big array), `deque` uses multiple small memory blocks and a "Map" (array of pointers) to track them.
```text
[ Block 1: A | B ]  [ Block 2: C | D ]  [ Block 3: E | F ]
       ^                   ^                   ^
       |___________________|___________________|
                           |
                     [ Map Array ]
```

---

## 3. The Logic Bridge
- **Hybrid Power:** It's the best choice for implementing **Queues** and **Stacks** because it doesn't require a massive reallocation/copy of all elements when it grows; it just allocates a new small block.
- **Iterator Catch:** Deque iterators are slower than vector iterators because they have to handle jumping between different memory blocks.
- **Random Access:** It supports `dq[5]`, but it's slightly slower than `v[5]` due to the double-pointer lookup.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Full Usage)

```cpp
#include <iostream>
#include <deque>

int main() {
    std::deque<int> dq = {10, 20, 30};

    // 1. Efficient End Ops
    dq.push_front(5);
    dq.push_back(35);

    // 2. Random Access
    std::cout << "Middle: " << dq[2] << std::endl;

    // 3. Modern Loop
    for (const auto& x : dq) std::cout << x << " ";

    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
