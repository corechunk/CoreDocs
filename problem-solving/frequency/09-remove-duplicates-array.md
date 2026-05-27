# 09 | Remove Duplicates from Array

Return a new array containing only unique elements.

---

## 1. The Objective
Given `[1, 2, 2, 3, 4, 4]`, return `[1, 2, 3, 4]`.

---

## 2. Visual Logic
### The "Unordered" vs "Ordered" Removal
- **Unordered:** Use a `std::unordered_set` (Fastest).
- **Ordered (Keep relative position):** Use a `std::unordered_set` to track history, but append only to a new vector.

---

## 3. The "Aha!" Moment
Removing duplicates is effectively a "Filter by History." You only let an element through if the Set has never seen it before.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>

/**
 * Strategy: History-tracking Filter (Maintains order)
 */
std::vector<int> removeDups(const std::vector<int>& arr) {
    std::unordered_set<int> seen;
    std::vector<int> res;
    for (int x : arr) {
        if (seen.find(x) == seen.end()) {
            res.push_back(x);
            seen.insert(x);
        }
    }
    return res;
}

int main() {
    std::vector<int> v = {10, 5, 10, 20, 5};
    auto res = removeDups(v);
    for (int x : res) std::cout << x << " ";
    return 0;
}
```
