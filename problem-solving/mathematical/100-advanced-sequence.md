# 100 | The Final Sequence: Ackermann Function

Explore one of the most recursive functions in existence.

---

## 1. The Objective
The **Ackermann Function** $A(m, n)$ is a famous example of a computable function that is not primitive recursive. It grows incredibly fast.
- $A(0, n) = n + 1$
- $A(m, 0) = A(m-1, 1)$
- $A(m, n) = A(m-1, A(m, n-1))$

---

## 2. Visual Logic
### The Growth
- $A(1, 2) = 4$
- $A(2, 2) = 7$
- $A(3, 2) = 29$
- $A(4, 2) = 2^{65536} - 3$ (Higher than atoms in the universe!)

---

## 3. The "Aha!" Moment
This function tests the limits of **Recursion** and the **Stack**. It is used to benchmarks how well a language or compiler handles deep recursive calls.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Deep Recursion
 * Warning: Stack overflow possible for m >= 4!
 */
int ackermann(int m, int n) {
    if (m == 0) return n + 1;
    if (m > 0 && n == 0) return ackermann(m - 1, 1);
    return ackermann(m - 1, ackermann(m, n - 1));
}

int main() {
    for (int m = 0; m <= 3; m++) {
        for (int n = 0; n <= 4; n++) {
            std::cout << "A(" << m << ", " << n << ") = " << ackermann(m, n) << std::endl;
        }
    }
    return 0;
}
```
