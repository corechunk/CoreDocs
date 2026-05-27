# 🔗 STL List (Doubly Linked)

## 1. The Objective
`std::list` is a doubly linked list. Unlike `vector`, it does not store elements in contiguous memory. Each element (node) points to its predecessor and successor. It excels at insertions and deletions at **any** position in $O(1)$ time, provided you already have an iterator to that position.

---

## 2. Visual Logic
### Node Structure
```text
[ Prev | Data | Next ] <-> [ Prev | Data | Next ]
```
- No random access: To get to the 5th element, you **must** traverse the first 4.

---

## 3. The Logic Bridge
- **Iterator Stability:** Unlike `vector`, adding or removing elements from a `list` **never** invalidates iterators to other elements. The nodes stay where they are in RAM; only the pointers between them change.
- **When to Use:** Use `list` ONLY if you need $O(1)$ middle-insertions on very large datasets or if you need absolute iterator stability. For everything else, `vector` is faster due to CPU cache locality.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Full Usage)

```cpp
#include <iostream>
#include <list>
#include <algorithm>

int main() {
    std::list<int> l = {10, 20, 30};

    // 1. Bidirectional Operations
    l.push_front(5);
    l.push_back(40);

    // 2. Middle Insertion
    auto it = std::find(l.begin(), l.end(), 20);
    if (it != l.end()) {
        l.insert(it, 15); // O(1)
    }

    // 3. Splice (Moving elements between lists in O(1))
    std::list<int> other = {100, 200};
    l.splice(l.begin(), other);

    for (int x : l) std::cout << x << " ";
    
    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
