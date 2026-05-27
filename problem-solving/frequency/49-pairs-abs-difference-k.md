# 49 | Pairs with Absolute Difference K

Count total pairs such that $|a - b| = K$.

---

## 1. The Objective
Given `[1, 1, 1, 2, 2]` and `K=0`, return `4`. (Pairs at indices `(0,1), (0,2), (1,2)` and `(3,4)`).

---

## 2. Visual Logic
### Method 1: The Multiplier (K=0)
If $K=0$, a value with frequency $f$ can form $\binom{f}{2}$ pairs.

### Method 2: The Cross-Map (K > 0)
For each unique value `x`, total pairs is `freq[x] * freq[x + K]`.

---

## 3. The "Aha!" Moment
By processing unique keys in the map, you can calculate the contribution of entire groups of numbers at once.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

int countDiffPairs(const std::vector<int>& nums, int k) {
    std::unordered_map<int, long long> freq;
    for (int x : nums) freq[x]++;
    
    int total = 0;
    for (auto const& [val, f] : freq) {
        if (k == 0) {
            total += (f * (f - 1)) / 2;
        } else {
            if (freq.count(val + k)) {
                total += f * freq[val + k];
            }
        }
    }
    return total;
}

int main() {
    std::vector<int> v = {1, 2, 2, 1};
    std::cout << "Diff 1 pairs: " << countDiffPairs(v, 1) << std::endl; // 1-2, 1-2, 2-1, 2-1 -> 4
    return 0;
}
```
