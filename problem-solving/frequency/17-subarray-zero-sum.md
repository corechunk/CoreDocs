# 17 | Subarray with Zero Sum

Check if any contiguous block of numbers adds up to exactly 0.

---

## 1. The Objective
Given `[4, 2, -3, 1, 6]`, return `true` because `2, -3, 1` sums to 0.

---

## 2. Visual Logic
### The "Prefix Sum" Strategy
Track the cumulative sum as you walk:
`Sum: 4 -> 6 -> 3 -> 4`
Look! The sum was `4` at index 0, and became `4` again at index 3.
This means everything between index 0 and 3 **canceled out to zero**.

---

## 3. The "Aha!" Moment
A zero-sum subarray exists if:
1. The prefix sum is 0 at any point.
2. The same prefix sum appears **twice**.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>

/**
 * Strategy: Hashed Prefix Sums
 */
bool hasZeroSumSubarray(const std::vector<int>& arr) {
    std::unordered_set<int> sums;
    int currentSum = 0;
    
    for (int x : arr) {
        currentSum += x;
        
        // Check if sum is 0 or if we've seen this sum before
        if (currentSum == 0 || sums.count(currentSum)) return true;
        
        sums.insert(currentSum);
    }
    return false;
}

int main() {
    std::vector<int> v = {4, 2, -3, 1, 6};
    std::cout << "Has zero sum? " << hasZeroSumSubarray(v) << std::endl;
    return 0;
}
```
