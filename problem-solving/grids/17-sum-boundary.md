# 17 | Sum of Boundary Elements

Calculate the total value of the matrix "shell".

---

## 1. The Objective
Sum all elements on the edges.

---

## 2. Visual Logic
Use the "Window Frame" logic from Problem 16 but add values to an accumulator instead of printing them.

---

## 3. The "Aha!" Moment
This excludes all "internal" values. For a $1000 \times 1000$ matrix, you only sum ~4000 elements instead of 1,000,000.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

long long sumBoundary(const std::vector<std::vector<int>>& grid) {
    int R = grid.size();
    int C = grid[0].size();
    long long sum = 0;
    
    for (int r = 0; r < R; r++) {
        for (int c = 0; c < C; c++) {
            if (r == 0 || r == R - 1 || c == 0 || c == C - 1) {
                sum += grid[r][c];
            }
        }
    }
    return sum;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 1, 1}, {1, 0, 1}, {1, 1, 1}};
    std::cout << "Boundary Sum: " << sumBoundary(mat) << std::endl;
    return 0;
}
```
