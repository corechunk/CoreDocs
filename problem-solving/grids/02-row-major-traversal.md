# 02 | Row-Major Traversal

Visit every element of a matrix row by row.

---

## 1. The Objective
Given a matrix, print its elements in the order they appear row by row.

---

## 2. Visual Logic
### The "Typewriter" Scan
```text
Row 0: [ 1 ] -> [ 2 ] -> [ 3 ]
Row 1: [ 4 ] -> [ 5 ] -> [ 6 ]
```
Output: `1 2 3 4 5 6`

---

## 3. The "Aha!" Moment
This is the default way computers store 2D arrays in memory (C-style). The outer loop controls the **Row Index**, and the inner loop controls the **Column Index**.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

/**
 * Strategy: Standard Row-wise nested loops
 */
void rowMajorPrint(const std::vector<std::vector<int>>& grid) {
    for (int r = 0; r < grid.size(); r++) {
        for (int c = 0; c < grid[r].size(); c++) {
            std::cout << grid[r][c] << " ";
        }
    }
    std::cout << std::endl;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2}, {3, 4}, {5, 6}};
    rowMajorPrint(mat);
    return 0;
}
```
