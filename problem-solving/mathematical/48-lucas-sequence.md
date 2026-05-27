# 48 | Lucas Sequence

Generate the Lucas series.

---

## 1. The Objective
The **Lucas Sequence** is very similar to Fibonacci but starts with **2** and **1**.
- $L_0 = 2$
- $L_1 = 1$
- $L_n = L_{n-1} + L_{n-2}$
- **Series:** $2, 1, 3, 4, 7, 11, 18, 29, \dots$

---

## 2. Visual Logic
### Relationship with Fibonacci
$L_n = F_{n-1} + F_{n+1}$.
The Lucas numbers represent the Golden Ratio just like Fibonacci, but they start with a higher "energy."

---

## 3. The "Aha!" Moment
Reuse your **Fibonacci Iterative** logic (Problem 01) but simply change the starting values of `a` and `b`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Iterative Sliding Window
 */
void printLucas(int n) {
    long long a = 2, b = 1;
    for (int i = 0; i < n; i++) {
        std::cout << a << " ";
        long long next = a + b;
        a = b;
        b = next;
    }
    std::cout << std::endl;
}

int main() {
    int n = 10;
    std::cout << "First 10 Lucas numbers: ";
    printLucas(n);
    return 0;
}
```
