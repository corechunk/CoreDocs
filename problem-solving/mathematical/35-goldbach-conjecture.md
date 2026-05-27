# 35 | Goldbach Conjecture

Every even integer greater than 2 is the sum of two prime numbers.

---

## 1. The Objective
Given an even number $n$, find two primes $p_1$ and $p_2$ such that $p_1 + p_2 = n$.
- **Example:** $10 = 3 + 7$.
- **Example:** $10 = 5 + 5$.

---

## 2. Visual Logic
### The "Search" Strategy (n=20)
1. Pick a prime $p$ starting from 2.
2. Check if $(n - p)$ is also a prime.
3. If YES, you found a pair.

- $p=2, n-p=18$ (No)
- $p=3, n-p=17$ (YES!) -> (3, 17)
- $p=5, n-p=15$ (No)
- $p=7, n-p=13$ (YES!) -> (7, 13)

---

## 3. The "Aha!" Moment
You only need to check primes $p$ up to $n/2$. If $(n-p)$ is also prime, the pair exists. This conjecture has been tested for numbers up to $4 \times 10^{18}$, but never formally proven for all numbers!

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

bool isPrime(int n) {
    if (n <= 1) return false;
    if (n <= 3) return true;
    if (n % 2 == 0 || n % 3 == 0) return false;
    for (int i = 5; i * i <= n; i += 6) {
        if (n % i == 0 || n % (i + 2) == 0) return false;
    }
    return true;
}

/**
 * Strategy: Complements Search
 */
void findGoldbachPairs(int n) {
    if (n <= 2 || n % 2 != 0) {
        std::cout << "Please enter an even number greater than 2." << std::endl;
        return;
    }

    std::cout << "Goldbach pairs for " << n << ":" << std::endl;
    for (int i = 2; i <= n / 2; i++) {
        if (isPrime(i) && isPrime(n - i)) {
            std::cout << n << " = " << i << " + " << n - i << std::endl;
        }
    }
}

int main() {
    findGoldbachPairs(20);
    return 0;
}
```
