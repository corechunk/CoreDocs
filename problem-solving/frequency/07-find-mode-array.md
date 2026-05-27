# 07 | Find Mode of Array

Identify the element that appears most frequently.

---

## 1. The Objective
Given `[1, 3, 3, 3, 2, 1]`, return `3`.

---

## 2. Visual Logic
### The "Leaderboard" Strategy
1. Build frequency map.
2. Track `maxFreq` and `modeValue`.
3. While building map, if `freq[x] > maxFreq`:
   - `maxFreq = freq[x]`
   - `modeValue = x`

---

## 3. The "Aha!" Moment
Mode is the "statistical peak." You can find it in a single $O(n)$ pass by updating the winner at every step.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

/**
 * Strategy: Concurrent Maximum Tracking
 */
int findMode(const std::vector<int>& arr) {
    std::unordered_map<int, int> freq;
    int mode = -1, maxF = 0;
    
    for (int x : arr) {
        freq[x]++;
        if (freq[x] > maxF) {
            maxF = freq[x];
            mode = x;
        }
    }
    return mode;
}

int main() {
    std::vector<int> v = {1, 2, 2, 3, 2, 4};
    std::cout << "Mode: " << findMode(v) << std::endl;
    return 0;
}
```
