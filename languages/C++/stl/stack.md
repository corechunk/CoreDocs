# 🥞 STL Stack - Master Reference

## 1. The Objective
`std::stack` is a container adapter that gives the programmer the functionality of a stack - specifically, a LIFO (Last-In, First-Out) data structure.

---

## 2. Visual Logic
### Restricted Interface
```text
[ User ] -> [ push / pop / top ] -> [ Underlying Container (Deque) ]
```

---

## 3. # The Logic Bridge (Key Points)

- **No Iterators:** You cannot iterate through a stack. You can only see the `top` element.
- **Exception Safety:** `pop()` returns `void`. This prevents data loss if a copy constructor throws while returning a value.
- **Container Options:** 
    - `std::stack<int>` (Uses Deque)
    - `std::stack<int, std::vector<int>>` (Uses Vector)
    - `std::stack<int, std::list<int>>` (Uses List)

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <stack>
#include <vector>

int main() {
    // --- 1. INITIALIZATION ---
    std::stack<int> s;
    std::stack<int, std::vector<int>> s_custom;

    // --- 2. CAPACITY ---
    if (s.empty()) std::cout << "Empty stack\n";
    size_t sz = s.size();

    // --- 3. MODIFIERS ---
    s.push(10);
    s.push(20);
    s.emplace(30);                         // Construct in-place

    // --- 4. ACCESS & REMOVAL ---
    std::cout << "Current Top: " << s.top() << "\n"; // 30
    s.pop();                               // Removes 30
    std::cout << "New Top: " << s.top() << "\n";     // 20

    // --- 5. SWAP ---
    std::stack<int> other;
    other.push(100);
    s.swap(other);                         // S now contains {100}

    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
