# 34 | Count Subarrays with Sum K

Find how many contiguous subarrays add up to a specific value.

---

## 1. The Objective
Given `[1, 1, 1]` and `K=2`, return `2`.

---

## 2. Visual Logic
### The "History of Sums" Map
For every prefix sum `S`, we want to know how many times the sum `S - K` has appeared in the past.
```text
Sum: 1 -> 2 -> 3
Looking for K=2:
At Sum=2: Need (2-2)=0. Was 0 seen? YES (init). Count=1.
At Sum=3: Need (3-2)=1. Was 1 seen? YES (at idx 0). Count=2.
```

---

## 3. The "Aha!" Moment
This is the advanced version of "Zero-sum Subarray." Using a frequency map of prefix sums allows you to count all matching gaps in one pass.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

int countSubarraysWithSum(const std::vector<int>& arr, int k) {
    std::unordered_map<int, int> sumFreq;
    sumFreq[0] = 1; // Base case
    int currentSum = 0, count = 0;
    
    for (int x : arr) {
        currentSum += x;
        if (sumFreq.count(currentSum - k)) {
            count += sumFreq[currentSum - k];
        }
        sumFreq[currentSum]++;
    }
    return count;
}

int main() {
    std::vector<int> v = {3, 4, 7, 2, -3, 1, 4, 2};
    std::cout << "Subarrays with sum 7: " << countSubarraysWithSum(v, 7) << std::endl;
    return 0;
}
```
