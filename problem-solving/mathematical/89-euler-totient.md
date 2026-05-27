# 89 | Euler's Totient Function (Phi)

Count numbers up to $n$ that are relatively prime to $n$.

---

## 1. The Objective
$\phi(n)$ counts the integers $k$ in range $1 \le k \le n$ for which $\text{GCD}(n, k) = 1$.
- **Example:** $\phi(9)$.
- Numbers: 1, 2, 3, 4, 5, 6, 7, 8, 9.
- Relatively prime to 9: 1, 2, 4, 5, 7, 8.
- Count: **6**.

---

## 2. Visual Logic
### Euler's Product Formula
$\phi(n) = n \prod_{p|n} (1 - \frac{1}{p})$
Where $p$ are distinct prime factors of $n$.
- $\phi(9) = 9 \times (1 - \frac{1}{3}) = 9 \times \frac{2}{3} = 6$.

---

## 3. The "Aha!" Moment
Instead of checking GCD for every number (slow), perform **Prime Factorization**. For every prime factor $p$, update the result: `res -= res / p`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Prime Factor Update
 * Efficiency: Time O(sqrt n)
 */
long long phi(long long n) {
    long long result = n;
    for (long long i = 2; i * i <= n; i++) {
        if (n % i == 0) {
            while (n % i == 0) n /= i;
            result -= result / i;
        }
    }
    if (n > 1) result -= result / n;
    return result;
}

int main() {
    std::cout << "Phi(9)  = " << phi(9) << std::endl;
    std::cout << "Phi(10) = " << phi(10) << std::endl;
    return 0;
}
```
