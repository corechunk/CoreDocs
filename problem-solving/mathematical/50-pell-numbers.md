# 50 | Pell Numbers

Generate the Pell sequence.

---

## 1. The Objective
The **Pell Sequence** is defined by the recurrence:
- $P_0 = 0$
- $P_1 = 1$
- $P_n = 2P_{n-1} + P_{n-2}$
- **Series:** $0, 1, 2, 5, 12, 29, 70, \dots$

---

## 2. Visual Logic
### The "Double-Weight" Step
Each number is the sum of the number before it **doubled**, plus the number before that.
- $P_2 = 2(1) + 0 = 2$
- $P_3 = 2(2) + 1 = 5$
- $P_4 = 2(5) + 2 = 12$

---

## 3. The "Aha!" Moment
This is a Fibonacci-variant where one of the previous terms has a "weight" of 2. It appears in the rational approximation of $\sqrt{2}$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Iterative Weighted Window
 */
void printPell(int n) {
    long long a = 0, b = 1;
    for (int i = 0; i < n; i++) {
        std::cout << a << " ";
        long long next = 2 * b + a;
        a = b;
        b = next;
    }
    std::cout << std::endl;
}

int main() {
    printPell(10);
    return 0;
}
```
