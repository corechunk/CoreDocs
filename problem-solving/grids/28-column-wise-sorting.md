# 28 | Column-wise Sorting

Sort each individual column of a matrix.

---

## 1. The Objective
Organize every column into ascending order.

---

## 2. Visual Logic
### The "Temporary Buffer" Strategy
1. For each column $c$:
   - Copy all elements `grid[0...R][c]` into a 1D vector.
   - Sort the vector.
   - Put elements back into the grid columns.

---

## 3. The "Aha!" Moment
Sorting columns is harder than rows because column elements are not contiguous in memory. You must manually extract and re-insert them.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

void sortCols(std::vector<std::vector<int>>& mat) {
    int rows = mat.size();
    int cols = mat[0].size();
    
    for (int c = 0; c < cols; c++) {
        std::vector<int> buffer;
        for (int r = 0; r < rows; r++) buffer.push_back(mat[r][c]);
        
        std::sort(buffer.begin(), buffer.end());
        
        for (int r = 0; r < rows; r++) mat[r][c] = buffer[r];
    }
}

int main() {
    std::vector<std::vector<int>> mat = {{10, 5}, {1, 9}};
    sortCols(mat);
    return 0;
}
```
