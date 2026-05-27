# 46 | Subarray with equal 0s and 1s

Find the longest contiguous block containing equal numbers of 0 and 1.

---

## 1. The Objective
Given `[0, 1, 0, 1, 1, 1, 0, 0]`, return `6` (indices 2 to 7).

---

## 2. Visual Logic
### The "Substitution" Trick
Treat `0` as `-1`. Now the problem is: "Find the longest subarray with **Sum = 0**."
1. Track prefix sum.
2. Store the **First Index** of each sum in a Map.
3. If sum repeats, calculate distance.

---

## 3. The "Aha!" Moment
Converting a "State Balance" problem into a "Zero Sum" problem is a powerful mathematical reduction. It allows you to reuse the prefix sum logic (Problem 39).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>
#include <algorithm>

int longestEqualSubarray(const std::vector<int>& nums) {
    std::unordered_map<int, int> firstSeen;
    firstSeen[0] = -1;
    int sum = 0, maxLen = 0;
    
    for (int i = 0; i < nums.size(); i++) {
        // Treat 0 as -1
        sum += (nums[i] == 0 ? -1 : 1);
        
        if (firstSeen.count(sum)) {
            maxLen = std::max(maxLen, i - firstSeen[sum]);
        } else {
            firstSeen[sum] = i;
        }
    }
    return maxLen;
}

int main() {
    std::vector<int> v = {0, 1, 0, 1, 1, 1, 0, 0};
    std::cout << "Longest equal subarray: " << longestEqualSubarray(v) << std::endl;
    return 0;
}
```
