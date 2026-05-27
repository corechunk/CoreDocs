# 09 | Horizontal Mirror

Flip a matrix along its horizontal central axis.

---

## 1. The Objective
Given:
```text
[ 1 | 2 ]
[ 3 | 4 ]
```
Result:
```text
[ 3 | 4 ]
[ 1 | 2 ]
```

---

## 2. Visual Logic
### The "Row Swap" Strategy
1. Row 0 swaps with Row $(R-1)$.
2. Row 1 swaps with Row $(R-2)$.
3. Stop at the middle.

---

## 3. The "Aha!" Moment
A horizontal flip is just a **reversal of the order of rows**. The contents of the rows (the columns) stay the same.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

/**
 * Strategy: Row Vector Swapping
 */
void flipHorizontal(std::vector<std::vector<int>>& grid) {
    int start = 0, end = grid.size() - 1;
    while (start < end) {
        std::swap(grid[start], grid[end]);
        start++;
        end--;
    }
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2}, {3, 4}};
    flipHorizontal(mat);
    // Row 0 is now 3, 4
    return 0;
}
```
