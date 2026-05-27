# 13 | Secondary Diagonal Sum

Calculate the sum of elements from top-right to bottom-left.

---

## 1. The Objective
Sum elements where `col index == (n - 1 - row index)`.

---

## 2. Visual Logic
```text
[ 1 | 2 | /3/ ]
[ 4 | /5/ | 6 ]
[ /7/ | 8 | 9 ]
Sum: 3 + 5 + 7 = 15
```

---

## 3. The "Aha!" Moment
Like the primary diagonal, this only needs one loop. The indices are always `grid[i][n - 1 - i]`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

int secondaryDiagSum(const std::vector<std::vector<int>>& grid) {
    int sum = 0;
    int n = grid.size();
    for (int i = 0; i < n; i++) {
        sum += grid[i][n - 1 - i];
    }
    return sum;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2}, {3, 4}};
    std::cout << "Secondary Sum: " << secondaryDiagSum(mat) << std::endl;
    return 0;
}
```
