# 🗺️ STL Map (Sorted Key-Value) - Master Reference

## 1. The Objective
`std::map` is a sorted associative container that contains key-value pairs with unique keys. Keys are sorted using a comparison function (usually `operator<`).

---

## 2. Visual Logic
### Balanced Tree Path
Searching for Key 80:
```text
          [ 50 ]
         /      \
      [ 20 ]    [ 80 ] (Match!)
```

---

## 3. # The Logic Bridge (Key Points)

- **Tree Property:** Iterating over a map is guaranteed to follow the order of the keys.
- **Lookup Cost:** $O(\log n)$. Slower than `unordered_map` but consistent and ordered.
- **Safe Insertion:** `insert` or `emplace` will not overwrite an existing key. `operator[]` **will** overwrite if the key exists, or **create** a default value if it doesn't.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Exhaustive Usage)

```cpp
#include <iostream>
#include <map>
#include <string>

int main() {
    // --- 1. INITIALIZATION ---
    std::map<std::string, int> m = {{"Alice", 20}, {"Bob", 25}};

    // --- 2. INSERTION ---
    m["Charlie"] = 30;                     // Map style (overwrites)
    m.insert({"David", 35});               // Pair style (doesn't overwrite)
    m.insert_or_assign("Alice", 21);       // C++17 Update
    m.emplace("Eve", 40);                  // Efficient construction

    // --- 3. LOOKUP ---
    if (m.count("Alice")) std::cout << "Alice exists\n";
    
    auto it = m.find("Bob");
    if (it != m.end()) {
        std::cout << "Bob is " << it->second << "\n";
    }

    // --- 4. BOUNDS (Sorted advantage) ---
    auto low = m.lower_bound("B");         // First element >= "B" (Bob)
    auto up = m.upper_bound("B");          // First element > "B" (Charlie)

    // --- 5. ERASURE ---
    m.erase("David");                      // By key
    m.erase(m.begin());                    // By iterator

    // --- 6. MODERN ITERATION (C++17) ---
    for (const auto& [name, age] : m) {
        std::cout << name << " -> " << age << "\n";
    }

    return 0;
}
```

---
[➔ Back to Associative Hub](02-associative-containers.md)
