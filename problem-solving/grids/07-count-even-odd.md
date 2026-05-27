# 07 | Count Even/Odd in Matrix

Calculate the parity distribution of numbers in a grid.

---

## 1. The Objective
Count how many even numbers and how many odd numbers are in the matrix.

---

## 2. Visual Logic
### The "Binning" Strategy
1. `evenCount = 0, oddCount = 0`
2. For each number:
   - `val % 2 == 0` ? `evenCount++` : `oddCount++`

---

## 3. The "Aha!" Moment
This combines grid traversal with the basic modulo logic from the Math tier.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void countParity(const std::vector<std::vector<int>>& grid) {
    int evens = 0, odds = 0;
    for (const auto& row : grid) {
        for (int val : row) {
            if (val % 2 == 0) evens++;
            else odds++;
        }
    }
    std::cout << "Evens: " << evens << ", Odds: " << odds << std::endl;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2, 3}, {4, 5, 6}};
    countParity(mat);
    return 0;
}
```
