# 46 | Arithmetic Progression (AP) Sum

Calculate the sum of a sequence with a constant difference.

---

## 1. The Objective
An **Arithmetic Progression** is a sequence where the difference between consecutive terms is constant ($d$).
- **Formula:** $a, a+d, a+2d, \dots$
- **Sum Formula:** $S_n = \frac{n}{2} [2a + (n-1)d]$
- **Example:** $5, 10, 15, 20$ (a=5, d=5, n=4). Sum = 50.

---

## 2. Visual Logic
### Tracing (a=2, d=3, n=5)
1. $2$
2. $2 + 3 = 5$
3. $5 + 3 = 8$
4. $8 + 3 = 11$
5. $11 + 3 = 14$
**Sum:** $2+5+8+11+14 = 40$.

---

## 3. The "Aha!" Moment
While you can loop through $n$ terms, the formula $O(1)$ is always preferred in programming to handle massive values of $n$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy A: Iterative Sum
 */
long long sumAPIterative(int a, int d, int n) {
    long long sum = 0;
    int current = a;
    for (int i = 0; i < n; i++) {
        sum += current;
        current += d;
    }
    return sum;
}

/**
 * Strategy B: Formula-based
 */
long long sumAPFormula(int a, int d, int n) {
    return (1LL * n * (2LL * a + (n - 1) * d)) / 2;
}

int main() {
    int a = 2, d = 3, n = 5;
    std::cout << "AP Sum (Iterative): " << sumAPIterative(a, d, n) << std::endl;
    std::cout << "AP Sum (Formula): " << sumAPFormula(a, d, n) << std::endl;
    return 0;
}
```
