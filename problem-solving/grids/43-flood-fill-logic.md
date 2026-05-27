# 43 | Flood Fill Logic

Change the "color" of an entire connected area.

---

## 1. The Objective
Similar to the "Bucket Tool" in MS Paint. If you click on a pixel, all neighboring pixels of the same color change to the new color.

---

## 2. Visual Logic
### Recursive Spread
1. Record original color.
2. If current pixel == original color:
   - Change to new color.
   - Call Flood Fill on neighbors.

---

## 3. The "Aha!" Moment
Flood Fill is just **BFS/DFS** in action. You must check that the new color is different from the old color, or you'll get an infinite loop!

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void floodFill(std::vector<std::vector<int>>& grid, int r, int c, int oldColor, int newColor) {
    if (r < 0 || r >= grid.size() || c < 0 || c >= grid[0].size()) return;
    if (grid[r][c] != oldColor || grid[r][c] == newColor) return;
    
    grid[r][c] = newColor;
    
    floodFill(grid, r + 1, c, oldColor, newColor);
    floodFill(grid, r - 1, c, oldColor, newColor);
    floodFill(grid, r, c + 1, oldColor, newColor);
    floodFill(grid, r, c - 1, oldColor, newColor);
}

int main() {
    std::vector<std::vector<int>> screen = {{1,1,1}, {1,1,0}, {1,0,1}};
    floodFill(screen, 1, 1, 1, 2);
    return 0;
}
```
