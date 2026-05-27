# 53 | Triangular Numbers

Generate numbers that can form an equilateral triangle.

---

## 1. The Objective
A **Triangular Number** counts objects arranged in an equilateral triangle.
- $1^{st} = 1$
- $2^{nd} = 1 + 2 = 3$
- $3^{rd} = 1 + 2 + 3 = 6$
- $n^{th} = \frac{n(n+1)}{2}$

---

## 2. Visual Logic
### The Shape of Numbers
```text
n=1:  * (1)

n=2:  *
     * * (3)

n=3:  *
     * *
    * * * (6)
```

---

## 3. The "Aha!" Moment
The $n^{th}$ triangular number is exactly the **Sum of first N natural numbers** (Problem 03).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Cumulative Sum
 */
void printTriangularNumbers(int limit) {
    int sum = 0;
    for (int i = 1; i <= limit; i++) {
        sum += i;
        std::cout << sum << " ";
    }
    std::cout << std::endl;
}

int main() {
    std::cout << "First 10 triangular numbers: ";
    printTriangularNumbers(10);
    return 0;
}
```
