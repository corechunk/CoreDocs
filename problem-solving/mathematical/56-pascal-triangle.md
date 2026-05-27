# 56 | Pascal's Triangle (Full)

Generate the complete Pascal's Triangle up to $n$ rows.

---

## 1. The Objective
Given `rows = 5`, generate the full matrix:
```text
    1
   1 1
  1 2 1
 1 3 3 1
1 4 6 4 1
```

---

## 2. Visual Logic
### The "Sum of Parents" Rule
Each number is the sum of the two numbers directly above it.
- Outside edges are always **1**.
- `Triangle[row][col] = Triangle[row-1][col-1] + Triangle[row-1][col]`

---

## 3. The "Aha!" Moment
This is a classic **Dynamic Programming** problem. You store previous results to calculate the next row. Use a 2D array or a `vector<vector<int>>`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <iomanip>

/**
 * Strategy: 2D Matrix DP
 * Efficiency: Time O(n^2), Space O(n^2)
 */
void printPascalTriangle(int rows) {
    std::vector<std::vector<long long>> triangle(rows, std::vector<long long>(rows));
    
    for (int i = 0; i < rows; i++) {
        // Formatting for triangle shape
        for (int space = 0; space < rows - i; space++) std::cout << "  ";
        
        for (int j = 0; j <= i; j++) {
            if (j == 0 || j == i) {
                triangle[i][j] = 1;
            } else {
                triangle[i][j] = triangle[i-1][j-1] + triangle[i-1][j];
            }
            std::cout << std::setw(4) << triangle[i][j];
        }
        std::cout << std::endl;
    }
}

int main() {
    printPascalTriangle(7);
    return 0;
}
```
