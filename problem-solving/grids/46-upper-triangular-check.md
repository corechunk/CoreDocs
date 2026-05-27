# 46 | Upper Triangular Matrix

Check if all elements below the primary diagonal are zero.

---

## 1. The Objective
In an **Upper Triangular Matrix**, $A_{ij} = 0$ if $i > j$.

---

## 2. Visual Logic
```text
[ 1 | 2 | 3 ]
[ 0 | 4 | 5 ]
[ 0 | 0 | 6 ]
```

---

## 3. The "Aha!" Moment
Only iterate through the "Lower Triangle" indices to verify they are zero.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

bool isUpperTriangular(const std::vector<std::vector<int>>& mat) {
    int n = mat.size();
    for (int i = 1; i < n; i++) {
        for (int j = 0; j < i; j++) {
            if (mat[i][j] != 0) return false;
        }
    }
    return true;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2}, {0, 3}};
    std::cout << "Upper Triangular? " << isUpperTriangular(mat) << std::endl;
    return 0;
}
```
