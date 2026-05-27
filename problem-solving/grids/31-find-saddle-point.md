# 31 | Find Saddle Point

Find an element that is minimum in its row and maximum in its column.

---

## 1. The Objective
Identify a "Saddle Point" $(r, c)$ where:
- `grid[r][c]` is the smallest in Row `r`.
- `grid[r][c]` is the largest in Col `c`.

---

## 2. Visual Logic
### The "Min-Max" Validation
1. For each row:
   - Find the min element and its column index `k`.
   - Check if that element is the maximum in column `k`.
   - If YES, found it!

---

## 3. The "Aha!" Moment
A matrix can have zero, one, or multiple saddle points. You must verify both conditions across the entire row and column.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void findSaddlePoint(const std::vector<std::vector<int>>& mat) {
    int n = mat.size();
    for (int i = 0; i < n; i++) {
        // Find min in row i
        int min_row = mat[i][0], col_idx = 0;
        for (int j = 1; j < n; j++) {
            if (mat[i][j] < min_row) {
                min_row = mat[i][j];
                col_idx = j;
            }
        }
        
        // Check if min_row is max in its column
        bool isSaddle = true;
        for (int k = 0; k < n; k++) {
            if (mat[k][col_idx] > min_row) {
                isSaddle = false;
                break;
            }
        }
        
        if (isSaddle) {
            std::cout << "Saddle Point: " << min_row << " at [" << i << "][" << col_idx << "]" << std::endl;
            return;
        }
    }
    std::cout << "No saddle point." << std::endl;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
    findSaddlePoint(mat);
    return 0;
}
```
