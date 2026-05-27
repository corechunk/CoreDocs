# 39 | Maximum Length Subarray with Sum K

Find the largest contiguous block that sums to $K$.

---

## 1. The Objective
Given `[1, -1, 5, -2, 3]` and `K=3`, return `4` (Subarray: `[1, -1, 5, -2]`).

---

## 2. Visual Logic
### The "First Seen" Map
1. Calculate prefix sums.
2. Map `sum -> index`.
3. If we find current sum `S`, and `S-K` was seen at `index_j`:
   - Current Length: `i - index_j`.
4. Only store the **First** time you see a specific sum to maximize length.

---

## 3. The "Aha!" Moment
This is Problem 34, but instead of counting frequency, we are looking for the maximum distance between sum occurrences.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>
#include <algorithm>

int maxSubArrayLen(const std::vector<int>& nums, int k) {
    std::unordered_map<int, int> firstSeen;
    firstSeen[0] = -1;
    int sum = 0, maxLen = 0;
    
    for (int i = 0; i < nums.size(); i++) {
        sum += nums[i];
        if (firstSeen.count(sum - k)) {
            maxLen = std::max(maxLen, i - firstSeen[sum - k]);
        }
        if (!firstSeen.count(sum)) {
            firstSeen[sum] = i;
        }
    }
    return maxLen;
}

int main() {
    std::vector<int> v = {1, -1, 5, -2, 3};
    std::cout << "Max Length for sum 3: " << maxSubArrayLen(v, 3) << std::endl;
    return 0;
}
```
