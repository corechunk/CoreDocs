# 28 | Co-prime Check

Determine if two numbers are relatively prime.

---

## 1. The Objective
Two numbers $a$ and $b$ are **Co-prime** (or relatively prime) if their greatest common divisor (GCD) is 1.
- **Example:** $8$ and $15$.
  - Divisors of 8: 1, 2, 4, 8
  - Divisors of 15: 1, 3, 5, 15
  - Common divisor: **1**. Result: **YES**.

---

## 2. Visual Logic
### The "Overlap" Check
Imagine two sets of prime factors. If they share **zero** factors, they are co-prime.
- $8 = 2 \times 2 \times 2$
- $15 = 3 \times 5$
- No common factors.

---

## 3. The "Aha!" Moment
You don't need to find all divisors. Just find the GCD (Problem 29). If $\text{GCD}(a, b) == 1$, then they are co-prime.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Euclidean Algorithm for GCD
 */
int gcd(int a, int b) {
    while (b != 0) {
        a %= b;
        std::swap(a, b);
    }
    return a;
}

/**
 * Strategy: GCD Verification
 */
bool areCoprime(int a, int b) {
    return gcd(a, b) == 1;
}

int main() {
    int x = 8, y = 15;
    
    if (areCoprime(x, y)) {
        std::cout << x << " and " << y << " are Co-prime." << std::endl;
    } else {
        std::cout << x << " and " << y << " are NOT Co-prime." << std::endl;
    }
    
    return 0;
}
```
