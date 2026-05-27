# ⚡ STL Unordered Map - Master Reference

## 1. The Objective
`std::unordered_map` is an associative container that contains key-value pairs with unique keys. Search, insertion, and removal of elements have average constant-time complexity.

---

## 2. Visual Logic
### Hash Buckets
```text
Key -> [Hash] -> Index
Index 4: [ {Alice, 20} -> {Zoe, 22} ] (Collision Chaining)
Index 7: [ {Bob, 25} ]
```

---

## 3. # The Logic Bridge (Key Points)

- **Average vs Worst Case:** While average is $O(1)$, a poorly designed hash function can cause $O(n)$ if all keys collide into the same bucket.
- **Load Factor:** `m.load_factor()` is the ratio of elements to buckets. When it exceeds `m.max_load_factor()`, a **Rehash** occurs (expensive $O(n)$ operation).
- **Pointer Stability:** Unlike `vector`, elements in an unordered_map are **not** moved during a rehash; only the bucket pointers change. Pointers to elements remain valid.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <unordered_map>
#include <string>

int main() {
    // --- 1. INITIALIZATION ---
    std::unordered_map<int, std::string> u = {{1, "One"}, {2, "Two"}};

    // --- 2. MODIFIERS ---
    u[3] = "Three";
    u.insert({4, "Four"});
    u.emplace(5, "Five");

    // --- 3. BUCKET INTERFACE (Tuning) ---
    std::cout << "Buckets: " << u.bucket_count() << "\n";
    std::cout << "Load: " << u.load_factor() << "\n";
    u.reserve(100);                         // Set bucket count for 100 elements

    // --- 4. LOOKUP ---
    if (u.contains(1)) {                    // C++20 check
        std::cout << "1 is here\n";
    }

    auto range = u.equal_range(2);          // Get iterators for specific key
    
    // --- 5. MODERN ITERATION ---
    for (auto const& [key, val] : u) {
        std::cout << key << ": " << val << " (Bucket " << u.bucket(key) << ")\n";
    }

    return 0;
}
```

---
[➔ Back to Associative Hub](02-associative-containers.md)
