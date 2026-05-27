# 32 | Continuous Subarray Sum Basics

Check if a subarray adds up to a multiple of $K$.

---

## 1. The Objective
Given `[23, 2, 4, 6, 7]` and `K=6`, return `true` (`2, 4` sums to 6).

---

## 2. Visual Logic
### The "Modulo Prefix" Strategy
Track prefix sum **modulo K**.
- `23 % 6 = 5`
- `(23+2) % 6 = 1`
- `(23+2+4) % 6 = 5` (Look! 5 appeared again).
This means the block between the first '5' and second '5' must sum to a multiple of 6.

---

## 3. The "Aha!" Moment
The modulo of a prefix sum is like a "Phase." If the phase repeats, a full cycle (a multiple of K) has been completed.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

bool checkSubarraySum(std::vector<int>& nums, int k) {
    std::unordered_map<int, int> modSeen;
    modSeen[0] = -1; // Handling edge case
    int sum = 0;
    
    for (int i = 0; i < nums.size(); i++) {
        sum += nums[i];
        int rem = sum % k;
        
        if (modSeen.count(rem)) {
            if (i - modSeen[rem] > 1) return true;
        } else {
            modSeen[rem] = i;
        }
    }
    return false;
}

int main() {
    std::vector<int> v = {23, 2, 4, 6, 7};
    std::cout << "Multiple of 6 subarray? " << checkSubarraySum(v, 6) << std::endl;
    return 0;
}
```
