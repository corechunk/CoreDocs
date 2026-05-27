# 12 | Primary Diagonal Sum

Calculate the sum of elements from top-left to bottom-right.

---

## 1. The Objective
In a square matrix, sum elements where `row index == col index`.

---

## 2. Visual Logic
```text
[ \1\ | 2 | 3 ]
[  4  | \5\ | 6 ]
[  7  | 8 | \9\ ]
Sum: 1 + 5 + 9 = 15
```

---

## 3. The "Aha!" Moment
You don't need nested loops! A single loop `for (int i = 0; i < n; i++)` can access all diagonal elements using `grid[i][i]`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

int primaryDiagSum(const std::vector<std::vector<int>>& grid) {
    int sum = 0;
    int n = grid.size();
    for (int i = 0; i < n; i++) {
        sum += grid[i][i];
    }
    return sum;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2}, {3, 4}};
    std::cout << "Primary Sum: " << primaryDiagSum(mat) << std::endl;
    return 0;
}
```
