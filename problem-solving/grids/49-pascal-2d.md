# 49 | Pascal's Triangle in 2D

Populate a matrix with the values of Pascal's Triangle.

---

## 1. The Objective
Map Pascal's Triangle into a 2D array format.

---

## 2. Visual Logic
```text
[ 1 | 0 | 0 ]
[ 1 | 1 | 0 ]
[ 1 | 2 | 1 ]
```
This is the same as the DP strategy from Problem 56 (Math).

---

## 3. The "Aha!" Moment
`mat[i][j] = mat[i-1][j-1] + mat[i-1][j]`. The zeros in the upper right handle the boundary naturally.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void fillPascal(int n) {
    std::vector<std::vector<int>> mat(n, std::vector<int>(n, 0));
    for (int i = 0; i < n; i++) {
        mat[i][0] = 1;
        for (int j = 1; j <= i; j++) {
            mat[i][j] = mat[i-1][j-1] + mat[i-1][j];
        }
    }
    // Print logic...
}

int main() {
    fillPascal(5);
    return 0;
}
```
