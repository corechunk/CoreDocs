# ⚡ STL Unordered Set (Unique Hashed)

## 1. The Objective
`std::unordered_set` is a hash-table-based container of unique keys. It provides $O(1)$ average-case performance for lookups. Use this when you need a "Presence Check" (Is $X$ in the set?) and don't care about the order.

---

## 2. Visual Logic
### Hash Table Presence
```text
Value: 50 -> Hash(50) -> Bucket 4 -> [ 50 ]
Value: 10 -> Hash(10) -> Bucket 1 -> [ 10 ]
```

---

## 3. The Logic Bridge
- **Speed Over Order:** It is significantly faster than `std::set` for large datasets but consumes more memory (to store the hash buckets).
- **Custom Objects:** To store a custom `struct` in an unordered set, you must define a custom hash function for it.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Full Usage)

```cpp
#include <iostream>
#include <unordered_set>

int main() {
    std::unordered_set<std::string> tags = {"cpp", "stl", "code"};

    // 1. $O(1)$ Check
    if (tags.find("stl") != tags.end()) {
        std::cout << "Tag found!\n";
    }

    // 2. Load and Efficiency
    std::cout << "Buckets: " << tags.bucket_count() << "\n";

    return 0;
}
```

---
[➔ Back to Associative Hub](02-associative-containers.md)
