# 27 | Row-wise Sorting

Sort each individual row of a matrix.

---

## 1. The Objective
Given:
```text
[ 3 | 1 | 2 ]
[ 9 | 4 | 6 ]
```
Result:
```text
[ 1 | 2 | 3 ]
[ 4 | 6 | 9 ]
```

---

## 2. Visual Logic
Treat each row as a separate 1D array and apply a standard sorting algorithm to it.

---

## 3. The "Aha!" Moment
`std::sort()` can be called on each `grid[i].begin()` and `grid[i].end()`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

void sortRows(std::vector<std::vector<int>>& mat) {
    for (int i = 0; i < mat.size(); i++) {
        std::sort(mat[i].begin(), mat[i].end());
    }
}

int main() {
    std::vector<std::vector<int>> mat = {{5, 1}, {9, 2}};
    sortRows(mat);
    return 0;
}
```
