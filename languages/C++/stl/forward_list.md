# ⛓️ STL Forward List (Singly Linked)

## 1. The Objective
`std::forward_list` is a singly linked list. It is designed to be the absolute **minimum memory** overhead linked structure in C++. It only points forward; there is no way to go back.

---

## 2. Visual Logic
### Singly Linked Structure
```text
[ Data | Next ] -> [ Data | Next ] -> NULL
```

---

## 3. The Logic Bridge
- **Minimalist Design:** It is more memory-efficient than `std::list` because it doesn't store a `prev` pointer. 
- **The "Before" Iterator:** Because you can't go back, many functions have "after" equivalents (e.g., `insert_after`, `erase_after`).
- **When to Use:** Use in highly memory-constrained environments where you need a linked list and will only ever traverse in one direction.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Full Usage)

```cpp
#include <iostream>
#include <forward_list>

int main() {
    std::forward_list<int> fl = {10, 20, 30};

    // 1. Efficient Insertion
    fl.push_front(5); // Only push_front is O(1)
    
    // 2. Insert After
    auto it = fl.begin(); // Points to 5
    fl.insert_after(it, 7); // [5, 7, 10, 20, 30]

    // 3. Removal
    fl.pop_front();

    for (int x : fl) std::cout << x << " ";

    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
