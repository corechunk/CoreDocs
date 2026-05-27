# 06 | All Elements Unique

Determine if an array has any duplicates.

---

## 1. The Objective
Given `[1, 2, 3, 4]`, return `true`. Given `[1, 2, 1]`, return `false`.

---

## 2. Visual Logic
### The "Set Size" Strategy
1. Put array into a Set.
2. Compare `set.size()` with `array.size()`.
3. If they are equal, everything was unique.

---

## 3. The "Aha!" Moment
You don't need a loop! The set constructor effectively acts as a filter. If the count drops, a duplicate was filtered out.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>

/**
 * Strategy: Set-Size Comparison
 */
bool isUnique(const std::vector<int>& arr) {
    std::unordered_set<int> s(arr.begin(), arr.end());
    return s.size() == arr.size();
}

int main() {
    std::vector<int> v = {1, 2, 3, 4, 2};
    std::cout << "All unique? " << isUnique(v) << std::endl;
    return 0;
}
```
