# 45 | Triplets with Sum Zero (3Sum)

Find all unique triplets $(a, b, c)$ such that $a+b+c = 0$.

---

## 1. The Objective
Given `[-1, 0, 1, 2, -1, -4]`, return `[[-1, -1, 2], [-1, 0, 1]]`.

---

## 2. Visual Logic
### The "Sorted Search" Strategy
1. Sort the array.
2. For each number `i`:
   - Use two pointers (`left`, `right`) to find pairs that sum to `-arr[i]`.
   - Skip duplicates to ensure results are unique.

---

## 3. The "Aha!" Moment
Combining **Sorting** and **Two Pointers** is often more memory-efficient than using a Map for the 3Sum problem, and handling duplicates becomes much easier.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

void findTriplets(std::vector<int>& nums) {
    std::sort(nums.begin(), nums.end());
    int n = nums.size();
    
    for (int i = 0; i < n - 2; i++) {
        if (i > 0 && nums[i] == nums[i-1]) continue; // Skip dups
        
        int l = i + 1, r = n - 1;
        while (l < r) {
            int sum = nums[i] + nums[l] + nums[r];
            if (sum == 0) {
                std::cout << "[" << nums[i] << ", " << nums[l] << ", " << nums[r] << "]" << std::endl;
                while (l < r && nums[l] == nums[l+1]) l++; // Skip dups
                while (l < r && nums[r] == nums[r-1]) r--; // Skip dups
                l++; r--;
            } else if (sum < 0) l++;
            else r--;
        }
    }
}

int main() {
    std::vector<int> v = {-1, 0, 1, 2, -1, -4};
    findTriplets(v);
    return 0;
}
```
