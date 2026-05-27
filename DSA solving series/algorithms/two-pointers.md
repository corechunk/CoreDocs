# ✌️ Two Pointers Technique

## 1. The Objective
The Two Pointers technique involves using two integer indices (pointers) to traverse a data structure (usually an array or linked list) simultaneously. It is primarily used to optimize $O(n^2)$ nested loops into **$O(n)$** linear scans.

---

## 2. Visual Logic
### Opposite Ends (Sorted Array Sum)
```text
Target = 10
[ 1 | 3 | 4 | 5 | 7 | 9 ]
  ^                   ^
  L                   R  (Sum=10! Found!)
```
- If Sum < Target, move `L` forward.
- If Sum > Target, move `R` backward.

---

## 3. The Logic Bridge
- **The "Monotonic" Constraint:** Two pointers usually works when the data has a sorted or monotonic property. Moving one pointer always changes the result in a predictable direction, allowing us to skip unnecessary comparisons.
- **Pointer Variants:**
    - **Collision:** Start at ends, move towards middle (e.g., Reverse string, TwoSum).
    - **Fast & Slow:** One moves twice as fast (e.g., Middle of LL, Cycle detection).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (TwoSum Sorted)

```cpp
#include <iostream>
#include <vector>

bool hasPairWithSum(const std::vector<int>& arr, int target) {
    int left = 0, right = arr.size() - 1;
    while (left < right) {
        int currentSum = arr[left] + arr[right];
        if (currentSum == target) return true;
        if (currentSum < target) left++;
        else right--;
    }
    return false;
}

int main() {
    std::vector<int> data = {1, 2, 4, 6, 8, 10};
    int target = 10;
    std::cout << "Target found: " << (hasPairWithSum(data, target) ? "Yes" : "No") << std::endl;
    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
