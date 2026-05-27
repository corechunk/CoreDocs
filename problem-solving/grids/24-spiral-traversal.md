# 24 | Spiral Traversal

Print a matrix in a clockwise spiral order.

---

## 1. The Objective
Given:
```text
1 2 3
4 5 6
7 8 9
```
Output: `1 2 3 6 9 8 7 4 5`

---

## 2. Visual Logic
### The "Closing Boundaries" Strategy
Keep 4 pointers: `top, bottom, left, right`.
1. Print **Top** row (left to right), increment `top`.
2. Print **Right** column (top to bottom), decrement `right`.
3. Print **Bottom** row (right to left), decrement `bottom`.
4. Print **Left** column (bottom to top), increment `left`.
5. Repeat until boundaries cross.

---

## 3. The "Aha!" Moment
Think of it like a snake eating itself. The "walls" of the snake's world shrink inward every time it finishes a straight line.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void printSpiral(const std::vector<std::vector<int>>& mat) {
    int top = 0, bottom = mat.size() - 1;
    int left = 0, right = mat[0].size() - 1;
    
    while (top <= bottom && left <= right) {
        // 1. Top row
        for (int i = left; i <= right; i++) std::cout << mat[top][i] << " ";
        top++;
        
        // 2. Right col
        for (int i = top; i <= bottom; i++) std::cout << mat[i][right] << " ";
        right--;
        
        // 3. Bottom row
        if (top <= bottom) {
            for (int i = right; i >= left; i--) std::cout << mat[bottom][i] << " ";
            bottom--;
        }
        
        // 4. Left col
        if (left <= right) {
            for (int i = bottom; i >= top; i--) std::cout << mat[i][left] << " ";
            left++;
        }
    }
    std::cout << std::endl;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}};
    printSpiral(mat);
    return 0;
}
```
