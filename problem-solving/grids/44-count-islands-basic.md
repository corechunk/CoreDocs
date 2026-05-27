# 44 | Count Islands (Basic)

Count the number of disconnected groups of '1's in a grid.

---

## 1. The Objective
Given a grid of land (1) and water (0), return the number of distinct islands.

---

## 2. Visual Logic
### The "Sinking" Strategy
1. Scan the grid.
2. When you find land (1):
   - Increment `islandCount`.
   - Use Flood Fill (Problem 43) to turn that entire island into water (0).
3. Continue scan.

---

## 3. The "Aha!" Moment
By "sinking" the island after you count it, you ensure that you don't count the same island twice as you continue your linear scan.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void sinkIsland(std::vector<std::vector<int>>& grid, int r, int c) {
    if (r < 0 || r >= grid.size() || c < 0 || c >= grid[0].size() || grid[r][c] == 0) return;
    grid[r][c] = 0;
    sinkIsland(grid, r+1, c); sinkIsland(grid, r-1, c);
    sinkIsland(grid, r, c+1); sinkIsland(grid, r, c-1);
}

int countIslands(std::vector<std::vector<int>> grid) {
    int count = 0;
    for (int r = 0; r < grid.size(); r++) {
        for (int c = 0; c < grid[0].size(); c++) {
            if (grid[r][c] == 1) {
                count++;
                sinkIsland(grid, r, c);
            }
        }
    }
    return count;
}

int main() {
    std::vector<std::vector<int>> world = {{1,1,0}, {1,0,0}, {0,0,1}};
    std::cout << "Islands: " << countIslands(world) << std::endl;
    return 0;
}
```
