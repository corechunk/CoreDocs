# 23 | Scalar Matrix Check

Verify if a matrix has the same constant on the primary diagonal and zeros elsewhere.

---

## 1. The Objective
A **Scalar Matrix** is a diagonal matrix where all diagonal elements are equal.
- **Example:**
```text
[ 5 | 0 | 0 ]
[ 0 | 5 | 0 ]
[ 0 | 0 | 5 ]
```

---

## 2. Visual Logic
1. First, check if it's a **Diagonal Matrix** (all non-diagonals are 0).
2. Second, pick the value at `[0][0]` and ensure all `[i][i]` match it.

---

## 3. The "Aha!" Moment
An Identity Matrix (Problem 19) is just a special type of Scalar Matrix where the constant is 1.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

bool isScalarMatrix(const std::vector<std::vector<int>>& mat) {
    int n = mat.size();
    int scalar = mat[0][0];
    
    for (int r = 0; r < n; r++) {
        for (int c = 0; c < n; c++) {
            if (r == c) {
                if (mat[r][c] != scalar) return false;
            } else {
                if (mat[r][c] != 0) return false;
            }
        }
    }
    return true;
}

int main() {
    std::vector<std::vector<int>> mat = {{7, 0}, {0, 7}};
    std::cout << "Scalar? " << isScalarMatrix(mat) << std::endl;
    return 0;
}
```
