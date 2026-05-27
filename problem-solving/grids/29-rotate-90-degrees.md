# 29 | Rotate Matrix 90 Degrees

Turn the entire matrix clockwise.

---

## 1. The Objective
Given a square matrix, rotate it 90 degrees in-place.

---

## 2. Visual Logic
### The "Transpose and Flip" Strategy
1. **Transpose** the matrix (rows become columns).
2. **Flip Horizontal** (reverse each row).

```text
Original:    Transpose:    Flip (Final):
1 2          1 3           3 1
3 4          2 4           4 2
```

---

## 3. The "Aha!" Moment
Instead of complex index mapping, use the building blocks you already learned (Problems 08 and 10).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

void rotate90(std::vector<std::vector<int>>& mat) {
    int n = mat.size();
    
    // 1. Transpose in-place
    for (int i = 0; i < n; i++) {
        for (int j = i; j < n; j++) {
            std::swap(mat[i][j], mat[j][i]);
        }
    }
    
    // 2. Reverse each row
    for (int i = 0; i < n; i++) {
        std::reverse(mat[i].begin(), mat[i].end());
    }
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2}, {3, 4}};
    rotate90(mat);
    return 0;
}
```
