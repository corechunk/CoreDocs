# 25 | Anti-Spiral Traversal

Print a matrix in an inward spiral starting from the center or counter-clockwise.

---

## 1. The Objective
Reverse the order of a standard spiral or traverse counter-clockwise.

---

## 2. Visual Logic
### The "Stack" Trick
1. Traverse the matrix in standard spiral order (Problem 24).
2. Instead of printing, push every element onto a **Stack**.
3. After the traversal, pop everything from the stack.
**Result:** Center to outside reverse spiral.

---

## 3. The "Aha!" Moment
Don't reinvent the wheel. If you have the forward path, you can use a stack to automatically find the reverse path.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <stack>

void printAntiSpiral(const std::vector<std::vector<int>>& mat) {
    std::stack<int> s;
    int top = 0, bottom = mat.size() - 1;
    int left = 0, right = mat[0].size() - 1;
    
    while (top <= bottom && left <= right) {
        for (int i = left; i <= right; i++) s.push(mat[top][i]); top++;
        for (int i = top; i <= bottom; i++) s.push(mat[i][right]); right--;
        if (top <= bottom) { for (int i = right; i >= left; i--) s.push(mat[bottom][i]); bottom--; }
        if (left <= right) { for (int i = bottom; i >= top; i--) s.push(mat[i][left]); left++; }
    }
    
    while (!s.empty()) {
        std::cout << s.top() << " ";
        s.pop();
    }
    std::cout << std::endl;
}

int main() {
    std::vector<std::vector<int>> mat = {{1, 2}, {3, 4}};
    printAntiSpiral(mat);
    return 0;
}
```
