# 48 | Divide into Pairs of K

Check if an array can be divided into pairs whose sum is divisible by $K$.

---

## 1. The Objective
Given `[1, 2, 3, 4, 5, 10, 6, 7, 8, 9]` and `K=5`, return `true`.

---

## 2. Visual Logic
### The "Remainder Matching"
1. Calculate `rem = x % K` for all items.
2. Map frequency of remainders.
3. For a pair to sum to a multiple of K:
   - If `rem = 0`: Must have an **Even** count (pairs with itself).
   - If `rem = r`: There must be an equal count of `K - r` remainders.

---

## 3. The "Aha!" Moment
The absolute values don't matter, only their "position" relative to the cycle of $K$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

bool canPair(std::vector<int>& nums, int k) {
    if (nums.size() % 2 != 0) return false;
    std::unordered_map<int, int> remFreq;
    
    for (int x : nums) remFreq[((x % k) + k) % k]++; // Handle negative modulo
    
    for (auto const& [rem, count] : remFreq) {
        if (rem == 0) {
            if (count % 2 != 0) return false;
        } else {
            if (remFreq[k - rem] != count) return false;
        }
    }
    return true;
}

int main() {
    std::vector<int> v = {1, 2, 3, 4, 5, 6};
    std::cout << "Can pair (K=7)? " << canPair(v, 7) << std::endl;
    return 0;
}
```
