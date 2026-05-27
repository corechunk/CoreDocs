# 11 | Square Matrix Check

Determine if a matrix has equal rows and columns.

---

## 1. The Objective
Check if $R == C$.

---

## 2. Visual Logic
```text
[ 1 | 2 ]
[ 3 | 4 ]  -> 2x2 (SQUARE)

[ 1 | 2 | 3 ]
[ 4 | 5 | 6 ]  -> 2x3 (RECTANGLE)
```

---

## 3. The "Aha!" Moment
Simple dimension check. Crucial because many matrix operations (like finding diagonals) only work on square matrices.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

bool isSquare(const std::vector<std::vector<int>>& grid) {
    if (grid.empty()) return true;
    return grid.size() == grid[0].size();
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 1}, {1, 1}};
    std::cout << "Square? " << isSquare(mat) << std::endl;
    return 0;
}
```
