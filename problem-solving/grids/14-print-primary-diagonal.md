# 14 | Print Primary Diagonal

Output only the elements on the top-left to bottom-right axis.

---

## 1. The Objective
Given a square matrix, display the diagonal line.

---

## 2. Visual Logic
### The "Identity" Trace
```text
i=0: mat[0][0]
i=1: mat[1][1]
...
```

---

## 3. The "Aha!" Moment
This is the same logic as Problem 12, but we print instead of sum. Useful for visualizing the "spine" of a matrix.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void printPrimary(const std::vector<std::vector<int>>& grid) {
    for (int i = 0; i < grid.size(); i++) {
        std::cout << grid[i][i] << " ";
    }
    std::cout << std::endl;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 0}, {0, 1}};
    printPrimary(mat);
    return 0;
}
```
