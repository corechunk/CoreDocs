# 🧮 Mathematical Algorithms

## 1. The Objective
Mathematical algorithms form the backbone of many complex systems, from **Cryptography** (RSA) to **Computer Graphics**. They focus on properties of numbers, primality, and modular arithmetic.

---

## 2. Visual Logic
### Sieve of Eratosthenes (Finding Primes)
```text
[ 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 ]
  ^
  |-- Mark multiples of 2 (4, 6, 8, 10) as Not Prime.
      ^
      |-- Mark multiples of 3 (6, 9) as Not Prime.
```

---

## 3. The Logic Bridge
- **The Euclidean Insight:** To find the GCD of two numbers $(A, B)$, we use the fact that `gcd(A, B) = gcd(B, A % B)`. This reduces large numbers to 0 in logarithmic time.
- **Fast Exponentiation:** To calculate $X^{64}$, don't multiply $X$ sixty-four times. Instead, calculate $X^{32}$ and square it. This turns $O(N)$ into **$O(\log N)$**.
- **Modular Arithmetic:** In competitive programming, we often take results `% 10^9+7`. This keeps numbers within the range of standard integers while preserving additive and multiplicative properties.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (GCD & Sieve)

```cpp
#include <iostream>
#include <vector>

// Euclidean Algorithm
int gcd(int a, int b) {
    return b == 0 ? a : gcd(b, a % b);
}

// Sieve of Eratosthenes
void sieve(int n) {
    std::vector<bool> isPrime(n + 1, true);
    isPrime[0] = isPrime[1] = false;
    for (int p = 2; p * p <= n; p++) {
        if (isPrime[p]) {
            for (int i = p * p; i <= n; i += p)
                isPrime[i] = false;
        }
    }
    std::cout << "Primes up to " << n << ": ";
    for (int p = 2; p <= n; p++) if (isPrime[p]) std::cout << p << " ";
    std::cout << "\n";
}

int main() {
    std::cout << "GCD of 48 and 18: " << gcd(48, 18) << std::endl;
    sieve(30);
    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
