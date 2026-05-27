# 11 | Pair with Given Sum (Two Sum)

Find two numbers that add up to a target value.

---

## 1. The Objective
Given `[2, 7, 11, 15]` and `target = 9`, return `true` (or indices `[0, 1]`).

---

## 2. Visual Logic
### The "Complement" Strategy
For every number `x`, we need to find if `target - x` exists.
1. As you walk through the array, calculate `needed = target - current`.
2. Look in your Set/Map: "Do I have `needed`?".
3. If YES: Done.
4. If NO: Put `current` in the Map and move on.

---

## 3. The "Aha!" Moment
Instead of searching for a pair ($O(n^2)$), you turn it into a "Look-Back" check. The Map acts as your memory of everything you have passed.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>

/**
 * Strategy: Hashed Complement Lookup
 */
bool hasPairWithSum(const std::vector<int>& arr, int target) {
    std::unordered_set<int> complements;
    for (int x : arr) {
        if (complements.count(target - x)) return true;
        complements.insert(x);
    }
    return false;
}

int main() {
    std::vector<int> v = {10, 5, 2, 3};
    std::cout << "Target 8 exists? " << hasPairWithSum(v, 8) << std::endl;
    return 0;
}
```
