# 🌲 STL Set (Unique Sorted)

## 1. The Objective
`std::set` is an associative container that contains a sorted set of unique objects of type `Key`. It is perfect for storing a collection of items where you need to quickly check for existence and keep the data sorted.

---

## 2. Visual Logic
### Balanced Tree (Red-Black)
```text
          [ 30 ]
         /      \
      [ 10 ]    [ 50 ]
```
- Adding `30` again will do nothing (Uniqueness).
- Iterating always yields: `10, 30, 50`.

---

## 3. The Logic Bridge
- **Binary Search internally:** Like `std::map`, a `std::set` uses a balanced tree. This makes searching for an element $O(\log n)$.
- **No Modification:** You cannot modify an element already in a set (it would break the sorted tree structure). You must erase it and insert the new value.
- **Multiset:** If you need to store duplicate sorted values, use `std::multiset`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Full Usage)

```cpp
#include <iostream>
#include <set>

int main() {
    std::set<int> s = {50, 10, 30, 10}; // 10 is duplicate

    // 1. Uniqueness check
    std::cout << "Size: " << s.size() << "\n"; // Size is 3

    // 2. Existence
    if (s.find(30) != s.end()) {
        std::cout << "30 exists.\n";
    }

    // 3. Lower Bound (First element >= X)
    auto it = s.lower_bound(20);
    std::cout << "First element >= 20: " << *it << "\n";

    for (int x : s) std::cout << x << " ";

    return 0;
}
```

---
[➔ Back to Associative Hub](02-associative-containers.md)
