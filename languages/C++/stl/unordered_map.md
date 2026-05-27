# ⚡ STL Unordered Map (Hash Table)

## 1. The Objective
`std::unordered_map` is a hash-table-based associative container. It provides **$O(1)$ average-case** performance for retrieval, making it the fastest choice for key-value lookups when order doesn't matter.

---

## 2. Visual Logic
### Hash Buckets
```text
Key: "Alice" -> Hash: 4 -> Bucket [4]: {"Alice", 25}
Key: "Bob"   -> Hash: 7 -> Bucket [7]: {"Bob", 30}
```

---

## 3. The Logic Bridge
- **Why "Unordered"?** Because hashing randomizes the distribution of keys, you have no guarantee of the order during iteration.
- **Bucket Collisions:** If two keys have the same hash, they are stored in a linked list at that bucket (Chaining). This can degrade performance to $O(n)$ in the worst possible case.
- **The "Load Factor" Rule:** The container automatically rehashes itself when it gets too full to keep lookups fast.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Full Usage)

```cpp
#include <iostream>
#include <unordered_map>

int main() {
    std::unordered_map<int, std::string> registry;

    // 1. Insertion
    registry[101] = "Admin";
    registry[202] = "Guest";

    // 2. Fast Lookup
    auto it = registry.find(101);
    if (it != registry.end()) {
        std::cout << "User 101: " << it->second << std::endl;
    }

    // 3. Bucket Info
    std::cout << "Buckets: " << registry.bucket_count() << "\n";
    std::cout << "Load Factor: " << registry.load_factor() << "\n";

    return 0;
}
```

---
[➔ Back to Associative Hub](02-associative-containers.md)
