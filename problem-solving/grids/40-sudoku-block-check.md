# 40 | Sudoku Block Check

Verify if a $3 \times 3$ Sudoku sub-grid is valid.

---

## 1. The Objective
Check if a specific $3 \times 3$ block contains digits 1-9 exactly once.

---

## 2. Visual Logic
### The "Frequency Set" Strategy
1. Create a boolean array `seen[10]`.
2. Iterate through the block.
3. If value is not between 1-9 OR is already `seen`, return false.

---

## 3. The "Aha!" Moment
Sudoku isn't just one big grid; it's 9 small grids. Mastering the indexing to jump between these blocks is the trick.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

bool isValidBlock(const std::vector<std::vector<int>>& board, int startR, int startC) {
    bool seen[10] = {false};
    for (int i = 0; i < 3; i++) {
        for (int j = 0; j < 3; j++) {
            int val = board[startR + i][startC + j];
            if (val < 1 || val > 9 || seen[val]) return false;
            seen[val] = true;
        }
    }
    return true;
}

int main() {
    // Example sub-grid...
    return 0;
}
```
