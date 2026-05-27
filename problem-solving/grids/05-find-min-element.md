# 05 | Find Minimum Element

Locate the smallest value in a 2D grid.

---

## 1. The Objective
Given a matrix, return the lowest number it contains.

---

## 2. Visual Logic
### The "Filter" Strategy
Start with the largest possible integer (`INT_MAX`) and "shrink" it every time you find a smaller number in the grid.

---

## 3. The "Aha!" Moment
Identical to Problem 04, just flipping the comparison operator.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <climits>

int findMin(const std::vector<std::vector<int>>& grid) {
    int minVal = INT_MAX;
    for (const auto& row : grid) {
        for (int val : row) {
            if (val < minVal) minVal = val;
        }
    }
    return minVal;
}

int main() {
    std::vector<std::vector<int>> mat = {{10, 50}, {5, 99}, {45, 12}};
    std::cout << "Min: " << findMin(mat) << std::endl;
    return 0;
}
```
