# ➕ Prefix Sums & Difference Arrays

## 1. The Objective
Prefix Sum is a preprocessing technique that allows calculating the **sum of any range $[L, R]$** in **$O(1)$** time. It trades a small amount of memory and $O(n)$ setup time for near-instant query performance.

---

## 2. Visual Logic
### Pre-calculation
```text
Original: [ 1 | 2 | 3 | 4 | 5 ]
Prefix:   [ 1 | 3 | 6 | 10| 15]
          (Prefix[i] = Sum of [0...i])
```
### Range Query [1, 3]
`Sum = Prefix[3] - Prefix[0]`
`Sum = 10 - 1 = 9` (Verified: 2+3+4 = 9)

---

## 3. The Logic Bridge
- **The "Cumulative" Power:** By storing the running total, every point in the prefix array acts as a snapshot of the sum up to that index.
- **Difference Array:** The inverse concept. To add $X$ to the range $[L, R]$, we set `Diff[L] += X` and `Diff[R+1] -= X`. When we take the prefix sum of the difference array, the update is applied across the whole range in $O(1)$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

class PrefixSum {
    std::vector<int> prefix;

public:
    PrefixSum(const std::vector<int>& arr) {
        int n = arr.size();
        prefix.resize(n);
        prefix[0] = arr[0];
        for (int i = 1; i < n; i++) prefix[i] = prefix[i - 1] + arr[i];
    }

    int query(int L, int R) {
        if (L == 0) return prefix[R];
        return prefix[R] - prefix[L - 1];
    }
};

int main() {
    std::vector<int> data = {1, 2, 3, 4, 5};
    PrefixSum ps(data);
    std::cout << "Sum of range [1, 3]: " << ps.query(1, 3) << std::endl;
    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
