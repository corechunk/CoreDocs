# 91 | Median of Sorted Arrays

Find the middle value of two combined sorted arrays.

---

## 1. The Objective
Given two sorted arrays `A` and `B`, find the median of the combined array.
- **Example:** `A = [1, 3]`, `B = [2]`. Combined: `[1, 2, 3]`. Median: **2**.
- **Example:** `A = [1, 2]`, `B = [3, 4]`. Combined: `[1, 2, 3, 4]`. Median: **2.5**.

---

## 2. Visual Logic
### The "Merge" Strategy
1. Use two pointers to merge the arrays into one sorted list (like Merge Sort).
2. If total size is odd, pick the middle.
3. If total size is even, average the two middle values.

---

## 3. The "Aha!" Moment
The naive way is $O(n+m)$ by merging. The "Pro" way (for interviews) uses Binary Search to find the partition point in $O(\log(\min(n,m)))$. Here we focus on the merge logic for clarity.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

/**
 * Strategy: Two-Pointer Merge
 * Efficiency: Time O(n+m)
 */
double findMedianSortedArrays(const std::vector<int>& nums1, const std::vector<int>& nums2) {
    std::vector<int> merged;
    int i = 0, j = 0;
    
    while (i < nums1.size() && j < nums2.size()) {
        if (nums1[i] < nums2[j]) merged.push_back(nums1[i++]);
        else merged.push_back(nums2[j++]);
    }
    while (i < nums1.size()) merged.push_back(nums1[i++]);
    while (j < nums2.size()) merged.push_back(nums2[j++]);
    
    int n = merged.size();
    if (n % 2 != 0) return merged[n/2];
    else return (merged[n/2 - 1] + merged[n/2]) / 2.0;
}

int main() {
    std::vector<int> a = {1, 3}, b = {2};
    std::cout << "Median: " << findMedianSortedArrays(a, b) << std::endl;
    return 0;
}
```
