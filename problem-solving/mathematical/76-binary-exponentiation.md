# 76 | Binary Exponentiation (Fast Power)

Calculate $a^b$ in $O(\log b)$ time.

---

## 1. The Objective
Given `a=2, b=10`, return `1024`.
Naive approach: $2 \times 2 \times \dots$ (10 times) is $O(b)$. We want the $O(\log b)$ way.

---

## 2. Visual Logic
### The "Divide and Conquer" Exponent
$2^{10} = (2^5)^2$
$2^5 = 2 \times (2^2)^2$
$2^2 = (2^1)^2$
$2^1 = 2 \times (2^0)^2$

Instead of multiplying 10 times, we only multiply when the exponent is odd, and square the base at every step.

---

## 3. The "Aha!" Moment
Every exponent can be broken down into powers of 2 (Binary).
$a^{13} = a^{1101_2} = a^8 \times a^4 \times a^1$.
By squaring the base ($a^1, a^2, a^4, a^8 \dots$), we can build any power in just $\log b$ steps.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Binary Exponentiation (Iterative)
 * Efficiency: Time O(log b), Space O(1)
 */
long long fastPower(long long a, long long b) {
    long long res = 1;
    while (b > 0) {
        // If exponent is odd, multiply result by current base
        if (b & 1) res = res * a;
        
        // Square the base and divide exponent by 2
        a = a * a;
        b >>= 1; // Equivalent to b / 2
    }
    return res;
}

int main() {
    std::cout << "2^10 = " << fastPower(2, 10) << std::endl;
    std::cout << "3^5  = " << fastPower(3, 5) << std::endl;
    return 0;
}
```
