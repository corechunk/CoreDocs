# 94 | Power Set Generation

Find all possible subsets of a given set.

---

## 1. The Objective
Given `{1, 2}`, return `{}, {1}, {2}, {1, 2}`.
Size of Power Set is $2^n$.

---

## 2. Visual Logic
### The "Binary Counter" Strategy
For a set of 3 elements, there are $2^3 = 8$ subsets.
Look at binary numbers 0 to 7:
- `000` -> `{}`
- `001` -> `{3}`
- `010` -> `{2}`
- `111` -> `{1, 2, 3}`
A subset exists where the bit is `1`.

---

## 3. The "Aha!" Moment
The power set generation is perfectly mapped to counting in binary. Each bit acts as an "In or Out" switch for that element.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <cmath>

/**
 * Strategy: Bit Manipulation
 * Efficiency: Time O(n * 2^n)
 */
void printPowerSet(const std::vector<int>& set) {
    int n = set.size();
    int powerSetSize = pow(2, n);
    
    for (int i = 0; i < powerSetSize; i++) {
        std::cout << "{ ";
        for (int j = 0; j < n; j++) {
            // Check if j-th bit of i is set
            if (i & (1 << j)) {
                std::cout << set[j] << " ";
            }
        }
        std::cout << "}" << std::endl;
    }
}

int main() {
    std::vector<int> s = {1, 2, 3};
    printPowerSet(s);
    return 0;
}
```
