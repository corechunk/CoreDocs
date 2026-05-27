# 50 | Magic Square Generator

Generate an $n \times n$ Magic Square for odd $n$.

---

## 1. The Objective
Create a square where all rows/cols/diagonals sum to the same constant.

---

## 2. Visual Logic
### The "Siamese Method"
1. Start at `[0][n/2]`.
2. Move **Up-Right** (`r-1, c+1`).
3. If out of bounds: Wrap around.
4. If cell occupied: Move **Down** instead.

---

## 3. The "Aha!" Moment
This simple deterministic rule creates a perfect Magic Square every time for odd numbers!

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <iomanip>

void generateMagicSquare(int n) {
    if (n % 2 == 0) return; // Odd only for this method
    
    std::vector<std::vector<int>> mat(n, std::vector<int>(n, 0));
    int r = 0, c = n / 2;
    
    for (int num = 1; num <= n * n; num++) {
        mat[r][c] = num;
        int nextR = (r - 1 + n) % n;
        int nextC = (c + 1) % n;
        
        if (mat[nextR][nextC] != 0) {
            r = (r + 1) % n;
        } else {
            r = nextR;
            c = nextC;
        }
    }
    
    // Print square
    for (auto const& row : mat) {
        for (int v : row) std::cout << std::setw(4) << v;
        std::cout << std::endl;
    }
}

int main() {
    generateMagicSquare(3);
    return 0;
}
```
