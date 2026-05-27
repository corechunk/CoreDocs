# 20 | Scalar Multiplication

Multiply every element of a matrix by a constant.

---

## 1. The Objective
Given a matrix and factor `k=5`, multiply every cell by 5.

---

## 2. Visual Logic
```text
5 * [ 1 | 2 ]  =  [ 5 | 10 ]
    [ 3 | 4 ]     [ 15 | 20 ]
```

---

## 3. The "Aha!" Moment
Simple nested loop traversal. The matrix structure doesn't change, only its content values.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void scaleMatrix(std::vector<std::vector<int>>& mat, int k) {
    for (auto& row : mat) {
        for (int& val : row) {
            val *= k;
        }
    }
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2}, {3, 4}};
    scaleMatrix(mat, 10);
    return 0;
}
```
