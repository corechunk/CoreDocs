# 35 | Neighbors Search (8-dir)

Identify all 8 surrounding cells (including diagonals).

---

## 1. The Objective
Find all neighbors of a cell in a $3 \times 3$ local block.

---

## 2. Visual Logic
### The "Nested Delta"
You can use two loops from `-1` to `1`.
```text
for dr in -1..1:
  for dc in -1..1:
    if dr==0 and dc==0: skip (center)
```

---

## 3. The "Aha!" Moment
The 8-neighbor logic is the engine for algorithms like **Minesweeper**, **Game of Life**, and **Image Blur filters**.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void printNeighbors8(const std::vector<std::vector<int>>& grid, int r, int c) {
    int R = grid.size();
    int C = grid[0].size();
    
    for (int i = -1; i <= 1; i++) {
        for (int j = -1; j <= 1; j++) {
            if (i == 0 && j == 0) continue;
            int nr = r + i, nc = c + j;
            if (nr >= 0 && nr < R && nc >= 0 && nc < C) {
                std::cout << grid[nr][nc] << " ";
            }
        }
    }
    std::cout << std::endl;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
    printNeighbors8(mat, 1, 1);
    return 0;
}
```
