# 54 | Catalan Numbers

Calculate numbers from the Catalan sequence.

---

## 1. The Objective
**Catalan Numbers** appear in many combinatorial problems (like valid bracket pairings).
- $C_n = \frac{1}{n+1} \binom{2n}{n}$
- **Series:** $1, 1, 2, 5, 14, 42, 132, \dots$

---

## 2. Visual Logic
### The "Valid Parentheses" Interpretation ($C_3=5$)
- `((()))`, `()(())`, `(())()`, `(()())`, `()()()`
Total: **5**.

---

## 3. The "Aha!" Moment
The recursive formula is: $C_{n+1} = \sum_{i=0}^{n} C_i C_{n-i}$.
However, for simple generation, using the formula $C_n = \frac{C_{n-1} \times (4n-2)}{n+1}$ is most efficient.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Iterative Formula
 * Efficiency: Time O(n)
 */
unsigned long long catalan(int n) {
    if (n <= 1) return 1;
    
    unsigned long long res = 1;
    for (int i = 1; i <= n; i++) {
        // C(i) = C(i-1) * (4*i - 2) / (i + 1)
        res = res * (4 * i - 2) / (i + 1);
    }
    return res;
}

int main() {
    for (int i = 0; i < 10; i++) {
        std::cout << "C(" << i << ") = " << catalan(i) << std::endl;
    }
    return 0;
}
```
