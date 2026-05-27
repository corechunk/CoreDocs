# 03 | Find Unique Element

Find the element that appears exactly once in an array where others appear twice.

---

## 1. The Objective
Given `[2, 3, 5, 4, 5, 3, 2]`, return `4`.

---

## 2. Visual Logic
### Method 1: The Map
Count frequencies. Return the one with count 1.

### Method 2: The XOR Magic
`x ^ x = 0`. If you XOR everything, all pairs vanish.
`2 ^ 3 ^ 5 ^ 4 ^ 5 ^ 3 ^ 2`
`= (2^2) ^ (3^3) ^ (5^5) ^ 4`
`= 0 ^ 0 ^ 0 ^ 4 = 4`.

---

## 3. The "Aha!" Moment
XOR is a "zero-memory" frequency tracker for pairs. It’s $O(1)$ space, while a map is $O(n)$ space.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

/**
 * Strategy: Bitwise XOR Cancellation
 * Efficiency: Time O(n), Space O(1)
 */
int findUnique(const std::vector<int>& arr) {
    int res = 0;
    for (int x : arr) res ^= x;
    return res;
}

int main() {
    std::vector<int> v = {7, 3, 5, 4, 5, 3, 4};
    std::cout << "Unique: " << findUnique(v) << std::endl; // 7
    return 0;
}
```
