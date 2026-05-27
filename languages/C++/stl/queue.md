# 👥 STL Queue (Adapter)

## 1. The Objective
`std::queue` is a container adapter that provides **FIFO** (First-In, First-Out) behavior. It restricts access to only the `front` (for removal) and the `back` (for insertion).

---

## 2. Visual Logic
### FIFO Restriction
```text
PUSH (Back) -> [ D | C | B | A ] -> POP (Front)
```

---

## 3. # The Logic Bridge (Key Points)

- **Underlying Container:** Uses `std::deque` by default. It **cannot** use `std::vector` because a queue needs `pop_front()`, which is $O(n)$ in a vector but $O(1)$ in a deque.
- **Use Case:** Perfect for producer-consumer patterns, BFS graph traversals, and task scheduling.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Full Usage)

```cpp
#include <iostream>
#include <queue>
#include <list>

int main() {
    // 1. Default Queue (deque)
    std::queue<std::string> q;

    // 2. Custom Queue (list)
    std::queue<int, std::list<int>> q_list;

    // 3. Operations
    q.push("First");
    q.push("Second");

    std::cout << "Front: " << q.front() << "\n"; // First
    std::cout << "Back: " << q.back() << "\n";   // Second

    q.pop();
    std::cout << "New Front: " << q.front() << "\n"; // Second

    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
