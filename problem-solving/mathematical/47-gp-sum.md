# 47 | Geometric Progression (GP) Sum

Calculate the sum of a sequence with a constant ratio.

---

## 1. The Objective
A **Geometric Progression** is a sequence where each term is found by multiplying the previous one by a constant ratio ($r$).
- **Formula:** $a, ar, ar^2, \dots$
- **Sum Formula:** $S_n = a \frac{1-r^n}{1-r}$
- **Example:** $2, 4, 8, 16$ (a=2, r=2, n=4). Sum = 30.

---

## 2. Visual Logic
### Tracing (a=3, r=2, n=4)
1. $3$
2. $3 \times 2 = 6$
3. $6 \times 2 = 12$
4. $12 \times 2 = 24$
**Sum:** $3+6+12+24 = 45$.

---

## 3. The "Aha!" Moment
GP sums grow very quickly. You must use `pow()` for the formula, but be careful of floating-point precision with very large ratios.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <cmath>

/**
 * Strategy A: Iterative Sum
 */
double sumGPIterative(double a, double r, int n) {
    double sum = 0;
    double current = a;
    for (int i = 0; i < n; i++) {
        sum += current;
        current *= r;
    }
    return sum;
}

/**
 * Strategy B: Formula-based
 */
double sumGPFormula(double a, double r, int n) {
    if (r == 1) return a * n;
    return a * (1 - pow(r, n)) / (1 - r);
}

int main() {
    double a = 3, r = 2;
    int n = 4;
    std::cout << "GP Sum (Iterative): " << sumGPIterative(a, r, n) << std::endl;
    std::cout << "GP Sum (Formula): " << sumGPFormula(a, r, n) << std::endl;
    return 0;
}
```
