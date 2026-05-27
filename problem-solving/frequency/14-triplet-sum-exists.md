# 14 | Triplet with Given Sum (Basics)

Find if three numbers add up to $K$.

---

## 1. The Objective
Given `[12, 3, 4, 1, 6, 9]` and `sum = 24`, return `true` (12, 3, 9).

---

## 2. Visual Logic
### The "Anchor" Strategy
1. Fix one element `x`.
2. Now the problem becomes finding a **Pair** with `sum = (K - x)`.
3. Use the Two-Sum logic (Problem 11) for the rest of the array.

---

## 3. The "Aha!" Moment
You reduce an $O(n^3)$ problem (3 loops) to $O(n^2)$ by using a Map/Set for the third element.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>

bool hasTriplet(const std::vector<int>& arr, int target) {
    int n = arr.size();
    for (int i = 0; i < n - 2; i++) {
        std::unordered_set<int> s;
        int current_target = target - arr[i];
        for (int j = i + 1; j < n; j++) {
            if (s.count(current_target - arr[j])) return true;
            s.insert(arr[j]);
        }
    }
    return false;
}

int main() {
    std::vector<int> v = {1, 4, 45, 6, 10, 8};
    std::cout << "Triplet sum 22? " << hasTriplet(v, 22) << std::endl;
    return 0;
}
```
