# 👥 STL Queue - Master Reference

## 1. The Objective
`std::queue` is a container adapter that provides FIFO (First-In, First-Out) behavior. It limits access to the front and back of the underlying container.

---

## 2. Visual Logic
### Order of Operations
```text
Push -> [ 3 | 2 | 1 ] -> Pop (1)
```

---

## 3. # The Logic Bridge (Key Points)

- **Vector Restriction:** You cannot use `std::vector` as the underlying container because a queue requires `pop_front()`, which vectors don't support efficiently ($O(n)$).
- **Default Choice:** `std::deque` is the default because it supports $O(1)$ operations at both ends.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <queue>
#include <list>

int main() {
    // --- 1. INITIALIZATION ---
    std::queue<int> q;
    std::queue<int, std::list<int>> q_list;

    // --- 2. CAPACITY ---
    bool b = q.empty();
    size_t s = q.size();

    // --- 3. MODIFIERS ---
    q.push(10);
    q.push(20);
    q.emplace(30);

    // --- 4. ACCESS ---
    std::cout << "Front: " << q.front() << "\n"; // 10
    std::cout << "Back: " << q.back() << "\n";   // 30

    // --- 5. REMOVAL ---
    q.pop();                                     // Removes 10
    std::cout << "New Front: " << q.front() << "\n"; // 20

    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
