# 42 | Basic Path Existence

Check if there is a path between two cells in a grid (unobstructed).

---

## 1. The Objective
Given a grid where `0` is empty and `1` is a wall, can you reach Point B from Point A?

---

## 2. Visual Logic
### The "Flood" Strategy
Start at A. "Flood" every reachable neighbor with color. If B gets colored, a path exists.

---

## 3. The "Aha!" Moment
This is an introduction to **DFS (Depth First Search)**. We use recursion to explore as far as possible along each branch.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

bool canReach(std::vector<std::vector<int>>& grid, int r, int c, int tr, int tc) {
    int R = grid.size(), C = grid[0].size();
    if (r < 0 || r >= R || c < 0 || c >= C || grid[r][c] != 0) return false;
    
    if (r == tr && c == tc) return true;
    
    grid[r][c] = -1; // Mark as visited
    
    return canReach(grid, r+1, c, tr, tc) || 
           canReach(grid, r-1, c, tr, tc) || 
           canReach(grid, r, c+1, tr, tc) || 
           canReach(grid, r, c-1, tr, tc);
}

int main() {
    std::vector<std::vector<int>> maze = {{0,1,0}, {0,0,1}, {1,0,0}};
    std::cout << "Path exists? " << canReach(maze, 0, 0, 2, 2) << std::endl;
    return 0;
}
```
