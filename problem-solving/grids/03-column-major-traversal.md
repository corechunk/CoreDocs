# 03 | Column-Major Traversal

Visit every element of a matrix column by column.

---

## 1. The Objective
Given a matrix, print elements starting from the first column downwards, then the second column, and so on.

---

## 2. Visual Logic
### The "Waterfall" Scan
```text
Col 0: [ 1 ]   Col 1: [ 2 ]
       [ 3 ]          [ 4 ]
       [ 5 ]          [ 6 ]
```
Output: `1 3 5 2 4 6`

---

## 3. The "Aha!" Moment
Swap the loops! The outer loop now controls the **Column Index**, and the inner loop controls the **Row Index**.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

/**
 * Strategy: Column-first nested loops
 */
void colMajorPrint(const std::vector<std::vector<int>>& grid) {
    if (grid.empty()) return;
    
    int rows = grid.size();
    int cols = grid[0].size();
    
    for (int c = 0; c < cols; c++) {
        for (int r = 0; r < rows; r++) {
            std::cout << grid[r][c] << " ";
        }
    }
    std::cout << std::endl;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2}, {3, 4}, {5, 6}};
    colMajorPrint(mat);
    return 0;
}
```
