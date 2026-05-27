# 04 | Find Maximum Element

Locate the largest value in a 2D grid.

---

## 1. The Objective
Given a matrix, return the highest number it contains.

---

## 2. Visual Logic
### The "Candidate" Strategy
1. Assume the first cell `[0][0]` is the maximum.
2. Visit every other cell.
3. If current cell $>$ max, update max.

---

## 3. The "Aha!" Moment
Like finding max in a 1D array, but you need two indices. This is the foundation for finding peak values in data sets.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <climits>

/**
 * Strategy: Linear Scan with Update
 */
int findMax(const std::vector<std::vector<int>>& grid) {
    int maxVal = INT_MIN;
    for (const auto& row : grid) {
        for (int val : row) {
            if (val > maxVal) maxVal = val;
        }
    }
    return maxVal;
}

int main() {
    std::vector<std::vector<int>> mat = {{10, 50}, {5, 99}, {45, 12}};
    std::cout << "Max: " << findMax(mat) << std::endl;
    return 0;
}
```
