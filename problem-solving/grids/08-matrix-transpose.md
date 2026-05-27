# 08 | Matrix Transpose

Flip a matrix over its primary diagonal.

---

## 1. The Objective
Given an $R \times C$ matrix, swap its rows with its columns to get a $C \times R$ matrix.
```text
[ 1 | 2 ]    ->    [ 1 | 3 | 5 ]
[ 3 | 4 ]          [ 2 | 4 | 6 ]
[ 5 | 6 ]
```

---

## 2. Visual Logic
### The "Index Swap" Rule
The element at `[r][c]` in the original matrix moves to `[c][r]` in the transposed matrix.

---

## 3. The "Aha!" Moment
Rows become columns. If your original grid was $3 \times 2$, your result will be $2 \times 3$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

/**
 * Strategy: New Matrix Allocation
 */
std::vector<std::vector<int>> transpose(const std::vector<std::vector<int>>& grid) {
    if (grid.empty()) return {};
    int rows = grid.size();
    int cols = grid[0].size();
    
    std::vector<std::vector<int>> res(cols, std::vector<int>(rows));
    
    for (int r = 0; r < rows; r++) {
        for (int c = 0; c < cols; c++) {
            res[c][r] = grid[r][c];
        }
    }
    return res;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2}, {3, 4}, {5, 6}};
    auto res = transpose(mat);
    // Print logic...
    return 0;
}
```
