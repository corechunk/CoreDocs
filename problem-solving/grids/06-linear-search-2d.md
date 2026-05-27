# 06 | Linear Search in 2D

Check if a specific value exists in a grid and return its coordinates.

---

## 1. The Objective
Given a target value `X`, find its Row and Column index.

---

## 2. Visual Logic
### The "Searchlight" Scan
Traverse row-by-row. If `grid[r][c] == target`, stop and return `(r, c)`.

---

## 3. The "Aha!" Moment
A search in 2D is still $O(N)$ where $N$ is the total number of cells. You must be prepared to handle the case where the value is **not** found (return -1, -1).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

/**
 * Strategy: Complete Grid Scan
 */
void searchIn2D(const std::vector<std::vector<int>>& grid, int target) {
    for (int r = 0; r < grid.size(); r++) {
        for (int c = 0; c < grid[r].size(); c++) {
            if (grid[r][c] == target) {
                std::cout << "Found " << target << " at [" << r << "][" << c << "]" << std::endl;
                return;
            }
        }
    }
    std::cout << "Not found." << std::endl;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2}, {3, 4}, {5, 6}};
    searchIn2D(mat, 4);
    return 0;
}
```
