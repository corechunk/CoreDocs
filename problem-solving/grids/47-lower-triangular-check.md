# 47 | Lower Triangular Matrix

Check if all elements above the primary diagonal are zero.

---

## 1. The Objective
$A_{ij} = 0$ if $i < j$.

---

## 2. Visual Logic
```text
[ 1 | 0 | 0 ]
[ 2 | 3 | 0 ]
[ 4 | 5 | 6 ]
```

---

## 3. The "Aha!" Moment
Opposite of Problem 46. Iterate through the "Upper Triangle."

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

bool isLowerTriangular(const std::vector<std::vector<int>>& mat) {
    int n = mat.size();
    for (int i = 0; i < n; i++) {
        for (int j = i + 1; j < n; j++) {
            if (mat[i][j] != 0) return false;
        }
    }
    return true;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 0}, {2, 3}};
    std::cout << "Lower Triangular? " << isLowerTriangular(mat) << std::endl;
    return 0;
}
```
