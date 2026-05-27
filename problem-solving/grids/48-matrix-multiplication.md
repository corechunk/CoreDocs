# 48 | Matrix Multiplication

Calculate the product of two matrices.

---

## 1. The Objective
Given $A$ ($R_a \times C_a$) and $B$ ($R_b \times C_b$), multiply them to get $C$ ($R_a \times C_b$).
**Rule:** $C_a$ must equal $R_b$.

---

## 2. Visual Logic
### The "Dot Product" Strategy
Each element $C[i][j]$ is the dot product of Row $i$ of A and Column $j$ of B.

---

## 3. The "Aha!" Moment
This requires **Triple Nested Loops**.
1. Outer: Target Row
2. Middle: Target Col
3. Inner: Accumulate dot product.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

std::vector<std::vector<int>> multiply(const std::vector<std::vector<int>>& A, const std::vector<std::vector<int>>& B) {
    int Ra = A.size(), Ca = A[0].size(), Cb = B[0].size();
    std::vector<std::vector<int>> res(Ra, std::vector<int>(Cb, 0));
    
    for (int i = 0; i < Ra; i++) {
        for (int j = 0; j < Cb; j++) {
            for (int k = 0; k < Ca; k++) {
                res[i][j] += A[i][k] * B[k][j];
            }
        }
    }
    return res;
}

int main() {
    // 2x2 multiplication example...
    return 0;
}
```
