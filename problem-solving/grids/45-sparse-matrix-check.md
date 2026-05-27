# 45 | Sparse Matrix Check

Determine if a matrix is mostly zeros.

---

## 1. The Objective
A matrix is **Sparse** if the majority of its elements are zero. Usually defined as `zeroCount > totalSize / 2`.

---

## 2. Visual Logic
Count zeros. Compare with `(rows * cols) / 2`.

---

## 3. The "Aha!" Moment
Sparse matrices are inefficient to store as 2D arrays. This check is the trigger for switching to **Sparse Storage** (like Coordinate List or CSR format).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

bool isSparse(const std::vector<std::vector<int>>& mat) {
    int zeros = 0;
    int total = mat.size() * mat[0].size();
    for (const auto& row : mat) {
        for (int val : row) if (val == 0) zeros++;
    }
    return zeros > (total / 2);
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 0, 0}, {0, 0, 2}, {0, 3, 0}};
    std::cout << "Sparse? " << isSparse(mat) << std::endl;
    return 0;
}
```
