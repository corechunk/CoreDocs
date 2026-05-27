# 🪟 Sliding Window

## 1. The Objective
Sliding Window is a technique used to perform operations on a specific **subarray or subsegment** of data. It converts nested $O(n^2)$ computations over sub-ranges into $O(n)$ by "sliding" the range and only updating the boundaries.

---

## 2. Visual Logic
### Fixed Window (Size = 3)
```text
[ 1 | 2 | 3 | 4 | 5 ]  Window: [1,2,3] Sum=6
    [ 2 | 3 | 4 ]      Slide: Add 4, Subtract 1. Sum=9
        [ 3 | 4 | 5 ]  Slide: Add 5, Subtract 2. Sum=12
```

---

## 3. The Logic Bridge
- **Incremental Update:** Instead of recalculating the whole window from scratch, we "reuse" the result from the previous window.
- **Variable vs. Fixed:** 
    - **Fixed:** Size remains constant (e.g., Max sum of $K$ elements).
    - **Variable:** Size expands/contracts based on a condition (e.g., Shortest subarray with sum $\ge X$).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Max Sum of K)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

int maxWindowSum(const std::vector<int>& arr, int k) {
    int n = arr.size();
    if (n < k) return -1;

    int currentSum = 0;
    for (int i = 0; i < k; i++) currentSum += arr[i];

    int maxSum = currentSum;
    for (int i = k; i < n; i++) {
        currentSum += arr[i] - arr[i - k]; // Slide!
        maxSum = std::max(maxSum, currentSum);
    }
    return maxSum;
}

int main() {
    std::vector<int> data = {2, 1, 5, 1, 3, 2};
    int k = 3;
    std::cout << "Max Window Sum: " << maxWindowSum(data, k) << std::endl;
    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
