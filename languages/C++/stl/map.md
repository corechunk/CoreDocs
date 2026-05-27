# 🗺️ STL Map (Sorted Key-Value)

## 1. The Objective
`std::map` is an associative container that stores key-value pairs. It is sorted by key and provides $O(\log n)$ time for search, insertion, and deletion.

---

## 2. Visual Logic
### Balanced BST (Red-Black Tree)
```text
          [ Key: 50 | Val: "A" ]
         /                      \
 [ Key: 20 | Val: "B" ]  [ Key: 80 | Val: "C" ]
```
- Keys are unique and strictly ordered.

---

## 3. The Logic Bridge
- **The "Order" Guarantee:** If you iterate through a `map`, the keys will always appear in sorted order.
- **Internal Structure:** It is almost always implemented as a **Red-Black Tree**. This guarantees $O(\log n)$ even if data is added in sorted order (unlike a raw BST).
- **Tradeoff:** It is slower than `unordered_map` because it must maintain the tree balance at every step.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Full Usage)

```cpp
#include <iostream>
#include <map>
#include <string>

int main() {
    // 1. Creation
    std::map<std::string, int> ages;

    // 2. Insertion Variants
    ages["Alice"] = 25; // Simple
    ages.insert({"Bob", 30});
    ages.emplace("Charlie", 35); // Efficient

    // 3. Safe Lookup
    if (ages.count("Alice")) {
        std::cout << "Alice is " << ages["Alice"] << "\n";
    }

    // 4. Modern Iteration (Structured Bindings C++17)
    for (const auto& [name, age] : ages) {
        std::cout << name << ": " << age << "\n";
    }

    return 0;
}
```

---
[➔ Back to Associative Hub](02-associative-containers.md)
