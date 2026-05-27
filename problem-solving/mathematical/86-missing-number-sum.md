# 86 | Find Missing Number (Sum Logic)

Find the missing element in a range $[1, n]$.

---

## 1. The Objective
Given an array of size $n-1$ containing distinct integers in the range $[1, n]$, find the one number that is missing.
- **Example:** Array: `[1, 2, 4, 5, 6]`. $n=6$. Missing: **3**.

---

## 2. Visual Logic
### The "Invariance" Strategy
If you have all numbers from 1 to $n$, their sum is $S_{total} = \frac{n(n+1)}{2}$.
If one number $x$ is missing, then:
$S_{actual} = S_{total} - x$
Therefore: $x = S_{total} - S_{actual}$.

---

## 3. The "Aha!" Moment
Math gives you the answer without searching! By comparing the **Theoretical Sum** with the **Actual Sum**, the difference "reveals" the missing piece.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <numeric>

/**
 * Strategy: Summation Difference
 * Efficiency: Time O(n), Space O(1)
 */
int findMissing(const std::vector<int>& arr, int n) {
    long long theoreticalSum = (1LL * n * (n + 1)) / 2;
    long long actualSum = std::accumulate(arr.begin(), arr.end(), 0LL);
    
    return (int)(theoreticalSum - actualSum);
}

int main() {
    std::vector<int> v = {1, 2, 4, 5, 6};
    std::cout << "Missing number: " << findMissing(v, 6) << std::endl;
    return 0;
}
```
