# 04 | Intersection of Two Arrays

Find all elements that appear in both arrays.

---

## 1. The Objective
Given `A = [1, 2, 2, 1]` and `B = [2, 2]`, return `[2]`.

---

## 2. Visual Logic
### The "Set Membership" Strategy
1. Put all elements of A into a `std::set` (removes duplicates).
2. For each element in B:
   - If it exists in the set, add to result and remove from set (to ensure result has no duplicates).

---

## 3. The "Aha!" Moment
A `Set` is just a HashMap where you only care about the keys, not the values. It allows for $O(1)$ existence checks.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>

/**
 * Strategy: Hashed Set Intersection
 */
std::vector<int> intersection(std::vector<int>& n1, std::vector<int>& n2) {
    std::unordered_set<int> s(n1.begin(), n1.end());
    std::vector<int> res;
    
    for (int x : n2) {
        if (s.count(x)) {
            res.push_back(x);
            s.erase(x); // Avoid duplicates in result
        }
    }
    return res;
}

int main() {
    std::vector<int> a = {1, 2, 2, 1}, b = {2, 2};
    auto res = intersection(a, b);
    for (int x : res) std::cout << x << " ";
    return 0;
}
```
