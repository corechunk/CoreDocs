# 26 | Zig-Zag (Snake) Traversal

Traverse a matrix in a back-and-forth snake-like pattern.

---

## 1. The Objective
Given:
```text
1 2 3
4 5 6
7 8 9
```
Output: `1 2 3 6 5 4 7 8 9`

---

## 2. Visual Logic
### The "Odd-Row Reverse" Strategy
1. For Row 0 (Even): Print Left-to-Right.
2. For Row 1 (Odd): Print Right-to-Left.
3. For Row 2 (Even): Print Left-to-Right.

---

## 3. The "Aha!" Moment
Use `if (row % 2 == 0)` to toggle the direction of the inner column loop.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void snakePrint(const std::vector<std::vector<int>>& mat) {
    for (int r = 0; r < mat.size(); r++) {
        if (r % 2 == 0) {
            for (int c = 0; c < mat[r].size(); c++) std::cout << mat[r][c] << " ";
        } else {
            for (int c = mat[r].size() - 1; c >= 0; c--) std::cout << mat[r][c] << " ";
        }
    }
    std::cout << std::endl;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2}, {3, 4}, {5, 6}};
    snakePrint(mat);
    return 0;
}
```
