# 05 | Union of Two Arrays

Find all unique elements from both arrays combined.

---

## 1. The Objective
Given `A = [1, 2]`, `B = [2, 3]`, return `[1, 2, 3]`.

---

## 2. Visual Logic
### The "Bucket" Strategy
1. Throw everything from A into a Set.
2. Throw everything from B into the same Set.
The Set automatically ignores any item that is already inside.

---

## 3. The "Aha!" Moment
Union is the simplest application of a Set. It represents the "Total Unique Space" of two datasets.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>

/**
 * Strategy: Cumulative Set Insertion
 */
std::vector<int> getUnion(const std::vector<int>& a, const std::vector<int>& b) {
    std::unordered_set<int> s;
    for (int x : a) s.insert(x);
    for (int x : b) s.insert(x);
    
    return std::vector<int>(s.begin(), s.end());
}

int main() {
    std::vector<int> a = {1, 2, 3}, b = {3, 4, 5};
    auto res = getUnion(a, b);
    for (int x : res) std::cout << x << " ";
    return 0;
}
```
