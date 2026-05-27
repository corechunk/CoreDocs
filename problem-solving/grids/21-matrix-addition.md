# 21 | Matrix Addition

Combine two matrices of the same dimensions.

---

## 1. The Objective
Add corresponding elements: `Result[r][c] = A[r][c] + B[r][c]`.

---

## 2. Visual Logic
```text
[ 1 | 2 ] + [ 5 | 6 ] = [ 6 | 8 ]
[ 3 | 4 ]   [ 7 | 8 ]   [ 10 | 12 ]
```

---

## 3. The "Aha!" Moment
The dimensions of A and B **must** be identical.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

std::vector<std::vector<int>> addMatrices(const std::vector<std::vector<int>>& A, const std::vector<std::vector<int>>& B) {
    int R = A.size();
    int C = A[0].size();
    std::vector<std::vector<int>> res(R, std::vector<int>(C));
    
    for (int r = 0; r < R; r++) {
        for (int c = 0; c < C; c++) {
            res[r][c] = A[r][c] + B[r][c];
        }
    }
    return res;
}

int main() {
    std::vector<std::vector<int>> A = {{1, 1}, {1, 1}};
    std::vector<std::vector<int>> B = {{2, 2}, {2, 2}};
    auto C = addMatrices(A, B);
    return 0;
}
```
