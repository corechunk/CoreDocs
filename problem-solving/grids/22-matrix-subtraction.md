# 22 | Matrix Subtraction

Calculate the difference between two matrices.

---

## 1. The Objective
`Result[r][c] = A[r][c] - B[r][c]`.

---

## 2. Visual Logic
Identical to addition, but use the `-` operator.

---

## 3. The "Aha!" Moment
This is essentially "Scalar Multiplication by -1" followed by addition.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

std::vector<std::vector<int>> subMatrices(const std::vector<std::vector<int>>& A, const std::vector<std::vector<int>>& B) {
    int R = A.size();
    int C = A[0].size();
    std::vector<std::vector<int>> res(R, std::vector<int>(C));
    
    for (int r = 0; r < R; r++) {
        for (int c = 0; c < C; c++) {
            res[r][c] = A[r][c] - B[r][c];
        }
    }
    return res;
}

int main() {
    // Usage...
    return 0;
}
```
