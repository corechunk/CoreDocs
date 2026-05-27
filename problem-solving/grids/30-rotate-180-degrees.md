# 30 | Rotate Matrix 180 Degrees

Turn the entire matrix upside down and left-to-right.

---

## 1. The Objective
Flip the matrix 180 degrees.

---

## 2. Visual Logic
### Method 1: Double Rotate
Apply the 90-degree rotation (Problem 29) twice.

### Method 2: Flip and Reverse
1. Flip the matrix horizontally (Row reversal order).
2. Reverse every individual row.

---

## 3. The "Aha!" Moment
A 180-degree rotation is identical to reversing the entire 1D representation of the matrix.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

void rotate180(std::vector<std::vector<int>>& mat) {
    // 1. Flip rows order (Horizontal flip)
    std::reverse(mat.begin(), mat.end());
    
    // 2. Reverse elements in each row (Vertical flip)
    for (auto& row : mat) {
        std::reverse(row.begin(), row.end());
    }
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2}, {3, 4}};
    rotate180(mat);
    return 0;
}
```
