# 01 | Sum of All Elements

Calculate the total sum of all numbers in a 2D grid.

---

## 1. The Objective
Given an $R \times C$ matrix, return the sum of all its elements.

---

## 2. Visual Logic
### The "Flattening" Strategy
Iterate through every row, and for each row, iterate through every column. Accumulate the values into a single variable.

```text
Grid (2x3):
[ 1 | 2 | 3 ] -> Row 1 Sum: 6
[ 4 | 5 | 6 ] -> Row 2 Sum: 15
Total: 6 + 15 = 21
```

---

## 3. The "Aha!" Moment
A 2D array is just an array of arrays. Two nested loops allow you to visit every "cell" exactly once.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

/**
 * Strategy: Nested Loop Accumulation
 * Efficiency: Time O(R*C), Space O(1)
 */
long long sumGrid(const std::vector<std::vector<int>>& grid) {
    long long total = 0;
    for (int i = 0; i < grid.size(); i++) {
        for (int j = 0; j < grid[i].size(); j++) {
            total += grid[i][j];
        }
    }
    return total;
}

int main() {
    std::vector<std::vector<int>> mat = {
        {1, 2, 3},
        {4, 5, 6}
    };
    std::cout << "Total Sum: " << sumGrid(mat) << std::endl;
    return 0;
}
```
