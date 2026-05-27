# 18 | Rotate Boundary Elements

Shift the shell of the matrix clockwise or anti-clockwise.

---

## 1. The Objective
Given:
```text
[ 1 | 2 | 3 ]
[ 4 | 5 | 6 ]
[ 7 | 8 | 9 ]
```
Rotate clockwise: `2` moves to `3` position, `3` moves to `6`, etc.

---

## 2. Visual Logic
### The "Circuit" Strategy
1. Unroll the boundary into a 1D list: `1, 2, 3, 6, 9, 8, 7, 4`.
2. Rotate the 1D list.
3. Repopulate the grid boundary using the rotated list.

---

## 3. The "Aha!" Moment
Treat the boundary like a circular track. This is the first step towards the "Spiral Matrix" (Problem 24).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

/**
 * Strategy: Temporary buffer shift
 */
void rotateBoundary(std::vector<std::vector<int>>& grid) {
    int R = grid.size();
    int C = grid[0].size();
    if (R < 2 || C < 2) return;
    
    int temp = grid[0][0];
    
    // Left col up
    for (int i = 0; i < R - 1; i++) grid[i][0] = grid[i+1][0];
    // Bottom row left
    for (int i = 0; i < C - 1; i++) grid[R-1][i] = grid[R-1][i+1];
    // Right col down
    for (int i = R - 1; i > 0; i--) grid[i][C-1] = grid[i-1][C-1];
    // Top row right
    for (int i = C - 1; i > 1; i--) grid[0][i] = grid[0][i-1];
    
    grid[0][1] = temp;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
    rotateBoundary(mat);
    // Boundary is now rotated clockwise
    return 0;
}
```
