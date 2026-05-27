# 🗺️ STL Containers (Associative)

## 1. The Objective
Associative containers store data in a sorted or hashed manner, allowing for very fast retrieval of values based on a **Key** rather than a position.

---

## 2. Visual Logic
- **`std::map` / `std::set`:** Balanced Binary Trees (Red-Black). Sorted by key. $O(\log n)$ lookup.
- **`std::unordered_map` / `std::unordered_set`:** Hash Tables. Unsorted. $O(1)$ average lookup.

---

## 3. The Logic Bridge
- **The "Sorted" Tradeoff:** Use `map` if you need to iterate through keys in order. Use `unordered_map` if you only care about speed and don't care about order.
- **Custom Keys:** To use a custom struct as a key in `map`, you must provide `operator<`. For `unordered_map`, you must provide a Hash function and `operator==`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Map vs Unordered)

```cpp
#include <iostream>
#include <map>
#include <unordered_map>

int main() {
    // 1. Sorted Map
    std::map<std::string, int> scores;
    scores["Core"] = 100;
    scores["Chunk"] = 90;

    // 2. Unordered (Hash Table)
    std::unordered_map<int, std::string> users;
    users[1] = "AI";

    std::cout << "Core Score: " << scores["Core"] << std::endl;
    return 0;
}
```

---
[➔ Back to STL Hub](00-stl-overview.md)
