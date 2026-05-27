# 87 | Find Duplicate (XOR Logic)

Find the duplicate number in an array using bitwise logic.

---

## 1. The Objective
Given an array of size $n+1$ containing integers from 1 to $n$, find the one number that appears twice.
- **Example:** `[1, 3, 4, 2, 2]`. $n=4$. Duplicate: **2**.

---

## 2. Visual Logic
### The "Cancellation" Strategy
The XOR operator has two magic properties:
1. `x ^ x = 0` (Identical values cancel out)
2. `x ^ 0 = x`

If we XOR all numbers in the array AND all numbers from 1 to $n$:
- Every number from 1 to $n$ appears **twice** (once in the range, once in the array).
- The duplicate number appears **three** times.
- Result: $(1 \dots n) \text{ pairs cancel to 0}$, leaving only the duplicate.

---

## 3. The "Aha!" Moment
XOR is like a "parity filter." It deletes everything that has a pair, leaving only the "odd one out" (the extra copy of the duplicate).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

/**
 * Strategy: XOR Cancellation
 * Efficiency: Time O(n), Space O(1)
 */
int findDuplicate(const std::vector<int>& arr, int n) {
    int xorSum = 0;
    
    // XOR all numbers in array
    for (int x : arr) xorSum ^= x;
    
    // XOR all numbers from 1 to n
    for (int i = 1; i <= n; i++) xorSum ^= i;
    
    return xorSum;
}

int main() {
    std::vector<int> v = {1, 3, 4, 2, 2};
    std::cout << "Duplicate number: " << findDuplicate(v, 4) << std::endl;
    return 0;
}
```
