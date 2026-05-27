# ⛓️ STL Forward List (Singly Linked) - Master Reference

## 1. The Objective
`std::forward_list` is a container that supports fast insertion and removal of elements from anywhere in the container. It is implemented as a singly linked list and is optimized for zero-memory overhead.

---

## 2. Visual Logic
### Forward-Only Chain
```text
[A]->[B]->[C]->[NULL]
```
- No `prev` pointers.
- No `size()` member function (to keep overhead at zero).

---

## 3. # The Logic Bridge (Key Points)

- **The "After" Logic:** Because you can only go forward, you can't insert "before" an iterator. You must use `insert_after`, `erase_after`, and `splice_after`.
- **Special Iterator:** `before_begin()` returns an iterator to the position before the first element, allowing insertion at the head using `insert_after`.
- **Memory King:** It is the most memory-efficient linked structure in C++.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <forward_list>
#include <algorithm>

int main() {
    // --- 1. INITIALIZATION ---
    std::forward_list<int> fl = {10, 20, 30};

    // --- 2. MODIFIERS ---
    fl.push_front(5);
    fl.emplace_front(0);
    fl.pop_front();

    // --- 3. "AFTER" OPERATIONS ---
    auto it = fl.begin(); // Points to 10
    fl.insert_after(it, 15);               // {10, 15, 20, 30}
    fl.erase_after(it);                    // Removes 15

    // --- 4. MEMBER ALGOS ---
    fl.sort();
    fl.reverse();
    fl.unique();
    fl.remove(20);

    // --- 5. HEAD INSERTION TRICK ---
    fl.insert_after(fl.before_begin(), 99);// Equivalent to push_front

    // --- 6. ITERATION ---
    for(int x : fl) std::cout << x << " ";

    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
