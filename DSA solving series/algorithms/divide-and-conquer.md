# ➗ Divide and Conquer

## 1. The Objective
Divide and Conquer is an algorithmic paradigm that breaks a problem into smaller subproblems, solves them independently, and then **combines** their results to solve the original problem.

---

## 2. Visual Logic
### The 3-Step Cycle
1. **Divide:** Split the problem into subproblems of the same type.
2. **Conquer:** Solve subproblems recursively.
3. **Combine:** Merge solutions (The hardest part).

```text
Problem (Size N)
      /      \
Sub(N/2)    Sub(N/2)
   |           |
Result <---- Result
```

---

## 3. The Logic Bridge
- **Recursion vs. D&C:** Recursion is the **tool**; Divide and Conquer is the **strategy**.
- **Master Theorem:** D&C performance is usually analyzed via the Master Theorem ($T(n) = aT(n/b) + f(n)$).
- **Classic Examples:** Merge Sort, Quick Sort, Binary Search, and Strassen's Matrix Multiplication.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Binary Search Style)

```cpp
#include <iostream>
#include <vector>

int findMax(const std::vector<int>& arr, int l, int r) {
    if (l == r) return arr[l];
    int mid = (l + r) / 2;
    return std::max(findMax(arr, l, mid), findMax(arr, mid + 1, r));
}

int main() {
    std::vector<int> data = {1, 5, 3, 9, 2};
    std::cout << "Max element: " << findMax(data, 0, data.size() - 1) << std::endl;
    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
