# 10 | Vertical Mirror

Flip a matrix along its vertical central axis.

---

## 1. The Objective
Given:
```text
[ 1 | 2 | 3 ]
[ 4 | 5 | 6 ]
```
Result:
```text
[ 3 | 2 | 1 ]
[ 6 | 5 | 4 ]
```

---

## 2. Visual Logic
### The "Internal Row Flip"
For every row in the matrix, reverse its contents.

---

## 3. The "Aha!" Moment
A vertical flip is just applying the **String Reverse** (Problem 02) logic to every row of the grid.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

/**
 * Strategy: Reverse each row sub-vector
 */
void flipVertical(std::vector<std::vector<int>>& grid) {
    for (auto& row : grid) {
        std::reverse(row.begin(), row.end());
    }
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2, 3}, {4, 5, 6}};
    flipVertical(mat);
    return 0;
}
```
