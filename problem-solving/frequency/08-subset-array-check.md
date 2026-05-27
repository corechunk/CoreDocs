# 08 | Subset Array Check

Check if array B is a subset of array A.

---

## 1. The Objective
Given `A = [1, 2, 3, 4, 5]` and `B = [2, 4]`, return `true`.

---

## 2. Visual Logic
### The "Search Optimization"
1. Put all elements of A in a Set.
2. For every element in B:
   - If not in set: Return `false`.
3. Return `true`.

---

## 3. The "Aha!" Moment
If you use a loop `for each b in B: for each a in A`, it's $O(N \times M)$. With a set, it's $O(N + M)$. Hashing turns nested loops into sequential loops.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>

/**
 * Strategy: Set Lookup
 */
bool isSubset(const std::vector<int>& A, const std::vector<int>& B) {
    std::unordered_set<int> s(A.begin(), A.end());
    for (int x : B) {
        if (s.find(x) == s.end()) return false;
    }
    return true;
}

int main() {
    std::vector<int> a = {1, 2, 3, 4, 5, 6}, b = {2, 5, 8};
    std::cout << "Is subset? " << isSubset(a, b) << std::endl;
    return 0;
}
```
