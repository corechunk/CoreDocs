# 33 | Skew-Symmetric Check

Check if $A^T = -A$.

---

## 1. The Objective
A matrix is skew-symmetric if $A_{ij} = -A_{ji}$ and diagonal elements are all **0**.

---

## 2. Visual Logic
```text
[  0 |  2 | -3 ]
[ -2 |  0 |  5 ]
[  3 | -5 |  0 ]
```

---

## 3. The "Aha!" Moment
The diagonal **must** be zero because $x = -x$ is only true for $x=0$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

bool isSkewSymmetric(const std::vector<std::vector<int>>& mat) {
    int n = mat.size();
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            if (i == j && mat[i][j] != 0) return false;
            if (mat[i][j] != -mat[j][i]) return false;
        }
    }
    return true;
}

int main() {
    std::vector<std::vector<int>> mat = {{0, 5}, {-5, 0}};
    std::cout << "Skew-Symmetric? " << isSkewSymmetric(mat) << std::endl;
    return 0;
}
```
