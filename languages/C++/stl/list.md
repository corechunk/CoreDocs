# 🔗 STL List (Doubly Linked) - Master Reference

## 1. The Objective
`std::list` is a sequence container that supports constant time insertion and removal of elements from anywhere in the container. Bidirectional traversal is supported, but no random access.

---

## 2. Visual Logic
### Linked Nodes
```text
[NULL|P]<-[A]->[N] <-> [P]<-[B]->[N] <-> [P]<-[C]->[N|NULL]
```

---

## 3. # The Logic Bridge (Key Points)

- **Pointer Stability:** Inserting or deleting an element does **not** invalidate pointers or iterators to other elements.
- **Member Algos:** Because of its non-contiguous nature, you must use member functions like `l.sort()`, `l.merge()`, `l.reverse()`, and `l.unique()` instead of the `<algorithm>` versions.
- **Splice:** The most unique feature. It can transfer nodes from one list to another in $O(1)$ by just changing pointers.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <list>
#include <algorithm>

int main() {
    // --- 1. CONSTRUCTORS ---
    std::list<int> l1 = {1, 2, 3, 4, 5};
    std::list<int> l2(3, 10);              // {10, 10, 10}

    // --- 2. ELEMENT ACCESS (No operator[]) ---
    int front = l1.front();
    int back = l1.back();

    // --- 3. MODIFIERS ---
    l1.push_front(0);
    l1.push_back(6);
    l1.emplace_front(-1);
    l1.emplace_back(7);
    
    l1.pop_front();
    l1.pop_back();

    auto it = std::find(l1.begin(), l1.end(), 3);
    l1.insert(it, 99);                     // Insert before 3
    l1.erase(it);                          // Remove 3

    // --- 4. LIST-ONLY OPERATIONS ---
    std::list<int> other = {100, 200};
    l1.splice(l1.begin(), other);          // Move other into l1 in O(1)
    
    l1.remove(99);                         // Remove all occurrences of 99
    l1.remove_if([](int n){ return n > 100; }); 
    
    l1.sort();                             // Member sort (O(n log n))
    l1.unique();                           // Remove consecutive duplicates
    l1.reverse();                          // Reverse order
    l1.merge(l2);                          // Merge two SORTED lists

    // --- 5. ITERATION ---
    for(int x : l1) std::cout << x << " ";

    return 0;
}
```

---
[➔ Back to Sequential Hub](01-sequential-containers.md)
