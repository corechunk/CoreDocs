# 🗺️ STL Containers (Associative)

## 1. The Objective
Associative containers store data in a sorted or hashed manner, allowing for very fast retrieval of values based on a **Key** rather than a position.

---

## 2. Visual Logic
### The Associative Split
- **Sorted (Tree-based):** `map`, `set`, `multimap`, `multiset`.
- **Hashed (Unordered):** `unordered_map`, `unordered_set`, etc.

---

## 3. # The Logic Bridge (Key Points)

### Performance Comparison
| Property | `map` / `set` | `unordered_map` / `unordered_set` |
| :--- | :--- | :--- |
| **Internal** | Red-Black Tree | Hash Table |
| **Lookup** | $O(\log n)$ | $O(1)$ Average / $O(n)$ Worst |
| **Order** | Strictly Sorted | No Order |
| **Requirements** | `operator<` | Hash Function & `operator==` |

### Key Selection Strategy
1. **Need Order?** Use `map` / `set`.
2. **Need Speed?** Use `unordered_map` / `unordered_set`.
3. **Duplicates Allowed?** Use `multi` versions.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Abstract Example)

```cpp
#include <iostream>
#include <map>
#include <unordered_map>

int main() {
    std::map<int, int> sorted;
    std::unordered_map<int, int> fast;

    std::cout << "Associative pillars initialized." << std::endl;
    return 0;
}
```

---

## 🔗 Granular Sub-Topics
- [std::map](map.md) - Sorted key-value pairs.
- [std::unordered_map](unordered_map.md) - Hashed key-value performance.
- [std::set](set.md) - Sorted unique keys.
- [std::unordered_set](unordered_set.md) - Hashed presence check.
- [Multi-Containers](multi-containers.md) - `multimap` & `multiset` (Duplicate keys).

[➔ Back to STL Hub](00-stl-overview.md)
