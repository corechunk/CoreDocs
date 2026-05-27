# 🌲 STL Set (Unique Sorted) - Master Reference

## 1. The Objective
`std::set` is an associative container that contains a sorted set of unique objects. It is effectively a `map` where the value is the same as the key.

---

## 2. Visual Logic
### Uniqueness Rule
```text
Set: { 10, 20, 30 }
Insert(20) -> Rejected (Already exists)
Insert(15) -> Re-balance -> { 10, 15, 20, 30 }
```

---

## 3. # The Logic Bridge (Key Points)

- **Immutable Keys:** Elements in a set are `const`. You cannot modify an element in-place because it would violate the sorting property. You must `extract()` (C++17), change, and re-insert.
- **Lookup:** $O(\log n)$.
- **Range Queries:** Sets excel at finding ranges of values using `lower_bound` and `upper_bound`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <set>

int main() {
    // --- 1. INITIALIZATION ---
    std::set<int> s = {3, 1, 4, 1, 5, 9};   // {1, 3, 4, 5, 9} (Unique)

    // --- 2. MODIFIERS ---
    s.insert(2);
    s.emplace(6);
    s.erase(1);                            // Remove by value
    
    // --- 3. LOOKUP & BOUNDS ---
    auto it = s.find(4);
    
    // Range: All elements between 2 and 5
    auto start = s.lower_bound(2);         // First element >= 2
    auto end = s.upper_bound(5);           // First element > 5

    // --- 4. ADVANCED: Extract (C++17) ---
    auto node = s.extract(3);              // Remove node without copying
    node.value() = 33;                     // Modify it
    s.insert(std::move(node));             // Re-insert

    // --- 5. ITERATION ---
    for (int x : s) std::cout << x << " ";

    return 0;
}
```

---
[➔ Back to Associative Hub](02-associative-containers.md)
