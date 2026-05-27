# 37 | Mersenne Prime

Check if a prime number is of the form $2^p - 1$.

---

## 1. The Objective
A **Mersenne Prime** is a prime number that is one less than a power of two ($M_p = 2^p - 1$).
- **Example:** $3$ ($2^2 - 1$)
- **Example:** $7$ ($2^3 - 1$)
- **Example:** $31$ ($2^5 - 1$)

---

## 2. Visual Logic
### The Power-Check Strategy
1. Check if $n$ is prime.
2. Check if $(n + 1)$ is a power of two.
   - Power of 2: $2, 4, 8, 16, 32, 64, \dots$
   - $(31 + 1) = 32$. (YES!)

---

## 3. The "Aha!" Moment
A number $x$ is a power of two if the bitwise operation `(x & (x - 1)) == 0`. This is the fastest way to verify a Mersenne prime candidate.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

bool isPrime(long long n) {
    if (n <= 1) return false;
    for (int i = 2; i * i <= n; i++) {
        if (n % i == 0) return false;
    }
    return true;
}

/**
 * Strategy: Bitwise Power Check
 */
bool isMersennePrime(long long n) {
    if (!isPrime(n)) return false;
    
    long long plusOne = n + 1;
    
    // Check if (n+1) is a power of 2 using bitwise trick
    return (plusOne > 0) && ((plusOne & (plusOne - 1)) == 0);
}

int main() {
    long long num = 127; // 2^7 - 1
    if (isMersennePrime(num)) std::cout << num << " is a Mersenne Prime." << std::endl;
    else std::cout << num << " is NOT a Mersenne Prime." << std::endl;
    return 0;
}
```
