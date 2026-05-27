# 49 | Tribonacci Sequence

A sequence where each term is the sum of the previous three.

---

## 1. The Objective
The **Tribonacci Sequence** starts with `0, 0, 1`.
- $T_0 = 0, T_1 = 0, T_2 = 1$
- $T_n = T_{n-1} + T_{n-2} + T_{n-3}$
- **Series:** $0, 0, 1, 1, 2, 4, 7, 13, 24, \dots$

---

## 2. Visual Logic
### The "Triple Window"
| Step | a | b | c | Sum (a+b+c) |
| :--- | :--- | :--- | :--- | :--- |
| Start | 0 | 0 | 1 | 1 |
| 1 | 0 | 1 | 1 | 2 |
| 2 | 1 | 1 | 2 | 4 |
| 3 | 1 | 2 | 4 | 7 |

---

## 3. The "Aha!" Moment
You need **three** variables to track the state instead of two. The sliding logic remains the same: `a=b, b=c, c=sum`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: 3-Variable Iterative Window
 */
void printTribonacci(int n) {
    if (n < 1) return;
    long long a = 0, b = 0, c = 1;
    
    if (n >= 1) std::cout << a << " ";
    if (n >= 2) std::cout << b << " ";
    if (n >= 3) std::cout << c << " ";
    
    for (int i = 4; i <= n; i++) {
        long long next = a + b + c;
        std::cout << next << " ";
        a = b;
        b = c;
        c = next;
    }
    std::cout << std::endl;
}

int main() {
    printTribonacci(10);
    return 0;
}
```
