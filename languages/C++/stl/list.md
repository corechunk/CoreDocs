# 🔗 STL List (Doubly Linked) - Full Usage

## 1. The Objective
`std::list` is a non-contiguous doubly linked list. It excels in scenarios where you need to move large chunks of data between lists or perform frequent insertions in the middle of a massive collection.

---

## 2. Visual Logic
### Node Isolation
```text
[P|A|N] <-> [P|B|N] <-> [P|C|N]
```
- Nodes are scattered in heap memory. Iterators just jump between addresses.

---

## 3. # The Logic Bridge (Key Points)

- **Absolute Stability:** Iterators and pointers to `std::list` elements are **never** invalidated, even if you add or remove other elements.
- **The "Splice" Advantage:** You can move elements from one list to another in **$O(1)$ time** just by re-linking pointers. `vector` would require $O(n)$ copying.
- **Member Algorithms:** Because `std::list` doesn't have Random Access iterators, you cannot use `std::sort(l.begin(), l.end())`. You **must** use the member function `l.sort()`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (The Complete API)

```cpp
#include <iostream>
#include <list>
#include <algorithm>

int main() {
    // --- 1. INITIALIZATION ---
    std::list<int> l1 = {10, 20, 30, 40, 50};

    // --- 2. MODIFIERS ---
    l1.push_front(5);
    l1.push_back(60);

    // --- 3. THE POWER OF SPLICE ---
    std::list<int> l2 = {100, 200};
    auto it = std::find(l1.begin(), l1.end(), 30);
    l1.splice(it, l2); // Moves all elements of l2 BEFORE 30 (O(1))

    // --- 4. MEMBER ALGORITHMS ---
    l1.sort();           // Custom sort for linked nodes
    l1.unique();         // Remove consecutive duplicates
    l1.reverse();        // Flip the list
    l1.remove(30);       // Remove all elements equal to 30

    // --- 5. ITERATION ---
    for (const auto& x : l1) std::cout << x << " ";

    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
