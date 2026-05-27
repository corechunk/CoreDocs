# 32 | Symmetric Matrix Check

Check if a matrix is equal to its own transpose.

---

## 1. The Objective
A matrix is symmetric if $A_{ij} = A_{ji}$ for all $i, j$.

---

## 2. Visual Logic
```text
[ 1 | 2 | 3 ]
[ 2 | 4 | 5 ]
[ 3 | 5 | 6 ]
```
Mirror elements across the primary diagonal are identical.

---

## 3. The "Aha!" Moment
You only need to check the "Upper Triangle" against the "Lower Triangle."

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

bool isSymmetric(const std::vector<std::vector<int>>& mat) {
    int n = mat.size();
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < i; j++) {
            if (mat[i][j] != mat[j][i]) return false;
        }
    }
    return true;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2}, {2, 1}};
    std::cout << "Symmetric? " << isSymmetric(mat) << std::endl;
    return 0;
}
```
