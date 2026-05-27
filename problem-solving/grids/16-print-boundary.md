# 16 | Print Boundary Elements

Display only the outer "frame" of a matrix.

---

## 1. The Objective
Given a matrix, print elements that are on the first row, last row, first column, or last column.

---

## 2. Visual Logic
### The "Window Frame"
```text
[ 1 | 2 | 3 ] <- First Row
[ 4 |   | 6 ] <- First/Last Col
[ 7 | 8 | 9 ] <- Last Row
```

---

## 3. The "Aha!" Moment
A cell `[r][c]` is a boundary element if:
- `r == 0` OR `r == rows-1`
- `c == 0` OR `c == cols-1`

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void printBoundary(const std::vector<std::vector<int>>& grid) {
    int R = grid.size();
    int C = grid[0].size();
    
    for (int r = 0; r < R; r++) {
        for (int c = 0; c < C; c++) {
            if (r == 0 || r == R - 1 || c == 0 || c == C - 1) {
                std::cout << grid[r][c] << " ";
            } else {
                std::cout << "  "; // Padding for inner empty space
            }
        }
        std::cout << std::endl;
    }
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
    printBoundary(mat);
    return 0;
}
```
