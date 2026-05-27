# ⚡ STL Unordered Set - Master Reference

## 1. The Objective
`std::unordered_set` is an associative container that contains a set of unique objects. Search, insertion, and removal have average constant-time complexity.

---

## 2. Visual Logic
### Membership Check
```text
Is 'X' in set?
Hash(X) -> Index 3 -> [ Y | Z ] (Check both) -> Result: NO
```

---

## 3. # The Logic Bridge (Key Points)

- **Primary Use Case:** When you only need to know "Does this element exist?" and order is irrelevant.
- **Custom Hashing:** To use a custom struct, you must specialize `std::hash<T>` or provide a hash function in the template.
- **Performance:** On average much faster than `std::set`, but slower to iterate through the entire collection due to non-contiguity and bucket overhead.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <unordered_set>
#include <string>

int main() {
    // --- 1. INITIALIZATION ---
    std::unordered_set<std::string> tags = {"cpp", "ai", "chunk"};

    // --- 2. MODIFIERS ---
    tags.insert("code");
    tags.emplace("stl");
    tags.erase("ai");

    // --- 3. LOOKUP ---
    if (tags.find("cpp") != tags.end()) {
        std::cout << "cpp found!\n";
    }

    if (tags.contains("chunk")) {           // C++20
        std::cout << "chunk found!\n";
    }

    // --- 4. BUCKETS ---
    std::cout << "Bucket count: " << tags.bucket_count() << "\n";
    
    // --- 5. ITERATION ---
    for (const auto& tag : tags) std::cout << tag << " ";

    return 0;
}
```

---
[➔ Back to Associative Hub](02-associative-containers.md)
