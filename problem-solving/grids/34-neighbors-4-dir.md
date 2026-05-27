# 34 | Neighbors Search (4-dir)

Identify adjacent cells (Up, Down, Left, Right).

---

## 1. The Objective
Given a coordinate $(r, c)$, find the values of its 4 orthogonal neighbors.

---

## 2. Visual Logic
### The "Delta" Arrays
Define shifts:
- Up: `(-1, 0)`
- Down: `(1, 0)`
- Left: `(0, -1)`
- Right: `(0, 1)`

---

## 3. The "Aha!" Moment
Always check boundaries! $(r+dr, c+dc)$ is only valid if it's within `[0, Rows-1]` and `[0, Cols-1]`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void printNeighbors4(const std::vector<std::vector<int>>& grid, int r, int c) {
    int R = grid.size();
    int C = grid[0].size();
    int dr[] = {-1, 1, 0, 0};
    int dc[] = {0, 0, -1, 1};
    
    std::cout << "Neighbors of [" << r << "][" << c << "]: ";
    for (int i = 0; i < 4; i++) {
        int nr = r + dr[i];
        int nc = c + dc[i];
        if (nr >= 0 && nr < R && nc >= 0 && nc < C) {
            std::cout << grid[nr][nc] << " ";
        }
    }
    std::cout << std::endl;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
    printNeighbors4(mat, 1, 1); // neighbors of 5
    return 0;
}
```
