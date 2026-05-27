# 19 | Identity Matrix Check

Verify if a square matrix is an Identity Matrix.

---

## 1. The Objective
An **Identity Matrix** has `1`s on the primary diagonal and `0`s everywhere else.

---

## 2. Visual Logic
```text
[ 1 | 0 | 0 ]
[ 0 | 1 | 0 ]
[ 0 | 0 | 1 ]
```

---

## 3. The "Aha!" Moment
Check every cell `grid[r][c]`.
- If `r == c`: Must be 1.
- Else: Must be 0.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

bool isIdentity(const std::vector<std::vector<int>>& mat) {
    int R = mat.size();
    int C = mat[0].size();
    if (R != C) return false;
    
    for (int r = 0; r < R; r++) {
        for (int c = 0; c < C; c++) {
            if (r == c && mat[r][c] != 1) return false;
            if (r != c && mat[r][c] != 0) return false;
        }
    }
    return true;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 0}, {0, 1}};
    std::cout << "Identity? " << isIdentity(mat) << std::endl;
    return 0;
}
```
