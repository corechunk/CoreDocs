# 88 | Magic Square Check

Verify if a 2D matrix is a Magic Square.

---

## 1. The Objective
A **Magic Square** is an $n \times n$ matrix where the sum of every row, every column, and both diagonals is the same constant.

---

## 2. Visual Logic
### Tracing (3x3)
```text
8 1 6  -> Sum: 15
3 5 7  -> Sum: 15
4 9 2  -> Sum: 15
| | |
15 15 15
Diag1 (8+5+2)=15, Diag2 (6+5+4)=15
```

---

## 3. The "Aha!" Moment
The "Magic Constant" for an $n \times n$ square using numbers $1 \dots n^2$ is $\frac{n(n^2+1)}{2}$. You must verify all $2n+2$ sums against this constant.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

/**
 * Strategy: Exhaustive Sum Verification
 */
bool isMagicSquare(const std::vector<std::vector<int>>& mat) {
    int n = mat.size();
    int magicSum = 0;
    for (int j = 0; j < n; j++) magicSum += mat[0][j];
    
    // Check rows
    for (int i = 1; i < n; i++) {
        int rowSum = 0;
        for (int j = 0; j < n; j++) rowSum += mat[i][j];
        if (rowSum != magicSum) return false;
    }
    
    // Check columns
    for (int j = 0; j < n; j++) {
        int colSum = 0;
        for (int i = 0; i < n; i++) colSum += mat[i][j];
        if (colSum != magicSum) return false;
    }
    
    // Check diagonals
    int diag1 = 0, diag2 = 0;
    for (int i = 0; i < n; i++) {
        diag1 += mat[i][i];
        diag2 += mat[i][n-1-i];
    }
    
    return (diag1 == magicSum && diag2 == magicSum);
}

int main() {
    std::vector<std::vector<int>> square = {
        {8, 1, 6},
        {3, 5, 7},
        {4, 9, 2}
    };
    if (isMagicSquare(square)) std::cout << "It's Magic!" << std::endl;
    return 0;
}
```
