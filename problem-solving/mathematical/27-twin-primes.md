# 27 | Twin Primes

Check if two numbers are twin primes or find twin primes in a range.

---

## 1. The Objective
**Twin Primes** are a pair of prime numbers that differ by exactly 2.
- **Example:** $(3, 5), (5, 7), (11, 13), (17, 19)$.

---

## 2. Visual Logic
### The "Double Check" Strategy
1. Pick a number $p$.
2. Check if $p$ is prime.
3. Check if $p+2$ is prime.
4. If both are YES, they are twins.

---

## 3. The "Aha!" Moment
Twin primes are always of the form $(p, p+2)$. In any range, you only need to check primes that are separated by one even number.

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
 * Strategy: Pairwise Primality Check
 */
void findTwinPrimes(int L, int R) {
    std::cout << "Twin Primes in range [" << L << ", " << R << "]:" << std::endl;
    for (int i = L; i <= R - 2; i++) {
        if (isPrime(i) && isPrime(i + 2)) {
            std::cout << "(" << i << ", " << i + 2 << ")" << std::endl;
        }
    }
}

int main() {
    findTwinPrimes(1, 100);
    return 0;
}
```
