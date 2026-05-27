# 13 | Pair with Given Difference

Find if two numbers exist such that $|a - b| = K$.

---

## 1. The Objective
Given `[5, 20, 3, 2, 50]` and `K = 15`, return `true` (20 and 5).

---

## 2. Visual Logic
### Two Possible Targets
For any `x`, the difference $K$ can be found if either `(x + K)` or `(x - K)` exists in the array.

---

## 3. The "Aha!" Moment
Similar to Two Sum, but instead of checking one complement, you check two "distance" points.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>

bool hasDiff(const std::vector<int>& arr, int k) {
    std::unordered_set<int> s;
    for (int x : arr) {
        if (s.count(x + k) || s.count(x - k)) return true;
        s.insert(x);
    }
    return false;
}

int main() {
    std::vector<int> v = {1, 8, 30, 40, 100};
    std::cout << "Diff 22 exists? " << hasDiff(v, 22) << std::endl;
    return 0;
}
```
