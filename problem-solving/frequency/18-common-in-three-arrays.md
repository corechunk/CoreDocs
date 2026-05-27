# 18 | Common Elements in Three Arrays

Find elements that exist in all three sorted arrays.

---

## 1. The Objective
Given `A=[1, 5, 10]`, `B=[3, 5, 20]`, `C=[5, 8, 15]`, return `[5]`.

---

## 2. Visual Logic
### Method 1: The Set Intersection
Intersection of A and B, then intersection of result and C.

### Method 2: Triple Pointers (If Sorted)
Check `A[i], B[j], C[k]`. If all equal, match. Else, increment the pointer of the smallest value.

---

## 3. The "Aha!" Moment
Hashing is the universal solution for unsorted data. If data is sorted, pointers are faster ($O(1)$ space).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>

/**
 * Strategy: Multi-set intersection
 */
std::vector<int> findCommon(std::vector<int>& a, std::vector<int>& b, std::vector<int>& c) {
    std::unordered_set<int> s1(a.begin(), a.end());
    std::unordered_set<int> s2(b.begin(), b.end());
    std::vector<int> res;
    
    for (int x : c) {
        if (s1.count(x) && s2.count(x)) {
            res.push_back(x);
            s1.erase(x); // Avoid dups
        }
    }
    return res;
}

int main() {
    std::vector<int> a={1,5,10}, b={5,10,20}, c={5,10};
    auto res = findCommon(a, b, c);
    for(int x : res) std::cout << x << " ";
    return 0;
}
```
