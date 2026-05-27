# 15 | Print Secondary Diagonal

Output the elements on the top-right to bottom-left axis.

---

## 1. The Objective
Display the anti-diagonal of a square matrix.

---

## 2. Visual Logic
```text
n=3
(0,2)
(1,1)
(2,0)
```

---

## 3. The "Aha!" Moment
The sum of indices $(r + c)$ is always equal to $(n-1)$ for every element on the secondary diagonal.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void printSecondary(const std::vector<std::vector<int>>& grid) {
    int n = grid.size();
    for (int i = 0; i < n; i++) {
        std::cout << grid[i][n - 1 - i] << " ";
    }
    std::cout << std::endl;
}

int main() {
    std::vector<std::vector<int>> mat = {{0, 1}, {1, 0}};
    printSecondary(mat);
    return 0;
}
```
