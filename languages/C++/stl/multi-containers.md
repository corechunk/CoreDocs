# 🌳 STL Multimap & Multiset - Master Reference

## 1. The Objective
`std::multimap` and `std::multiset` are associative containers that behave exactly like their standard counterparts, except they **allow duplicate keys**. They are essential for handling "One-to-Many" relationships (e.g., a dictionary where one word has multiple definitions).

---

## 2. Visual Logic
### Duplicate Key Structure
```text
Key: "A" -> Value: 10
Key: "A" -> Value: 20
Key: "B" -> Value: 30
```
- In-order traversal: `A(10), A(20), B(30)`.

---

## 3. # The Logic Bridge (Key Points)

- **The "Equal Range" Power:** Because keys are duplicated, `find()` only returns an iterator to **one** of the instances. To get all instances, you must use `equal_range()`, which returns a pair of iterators (start and end of the key block).
- **No `operator[]`:** Multimaps **do not** support the `[]` operator. Why? Because `m[key]` is ambiguous when multiple values exist for that key. You must use `insert()` or `emplace()`.
- **Complexity:** Remains **$O(\log n)$** for all major operations.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <map>
#include <set>
#include <string>

int main() {
    // --- 1. MULTIMAP (One-to-Many) ---
    std::multimap<std::string, int> m;
    m.insert({"Error", 404});
    m.insert({"Error", 500});
    m.emplace("Warning", 200);

    // Finding all values for "Error"
    auto range = m.equal_range("Error");
    for (auto it = range.first; it != range.second; ++it) {
        std::cout << it->first << ": " << it->second << "\n";
    }

    // --- 2. MULTISET (Duplicates allowed) ---
    std::multiset<int> s = {10, 20, 10, 30};
    
    // Count specific occurrences
    std::cout << "Count of 10s: " << s.count(10) << "\n"; // Output: 2

    // Erasing all instances vs one instance
    // s.erase(10);           // Removes ALL 10s
    // s.erase(s.find(10));   // Removes ONLY one 10

    return 0;
}
```

---
[➔ Back to Associative Hub](02-associative-containers.md)
