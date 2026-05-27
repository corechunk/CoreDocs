# 🥞 STL Stack (Adapter)

## 1. The Objective
`std::stack` is a **Container Adapter**. It isn't a standalone data structure; instead, it takes an existing container (like `deque` or `vector`) and limits its interface to provide **LIFO** (Last-In, First-Out) behavior.

---

## 2. Visual Logic
### The Wrapper Pattern
```text
[ User ] -> [ Stack API (push/pop) ] -> [ Underlying Deque ]
```

---

## 3. # The Logic Bridge (Key Points)

- **Default Underlay:** By default, `std::stack` uses `std::deque`. Why? Because `deque` allocates memory in blocks and doesn't require a full re-allocation/copy when it grows.
- **Switching Bases:** You can tell a stack to use a `vector` or `list` instead: `std::stack<int, std::vector<int>> s;`.
- **Top Safety:** `pop()` in STL **does not return the value**. You must call `top()` to get the value and then `pop()` to remove it. This ensures exception safety.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Full Usage)

```cpp
#include <iostream>
#include <stack>
#include <vector>

int main() {
    // 1. Default Stack (using deque)
    std::stack<int> s;

    // 2. Custom Stack (using vector)
    std::stack<int, std::vector<int>> s_vec;

    // 3. Operations
    s.push(10);
    s.emplace(20); // Construct in-place
    
    std::cout << "Top: " << s.top() << "\n";
    
    s.pop(); // Remove 20
    std::cout << "New Top: " << s.top() << "\n";

    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
