# 25 | Prime Factors

Find all prime numbers that divide a given number $n$.

---

## 1. The Objective
Given `12`, return `2, 2, 3` (because $2 \times 2 \times 3 = 12$).

---

## 2. Visual Logic
### The "Divide and Conquer" Strategy (n=315)
- Is 315 divisible by 2? NO.
- Is 315 divisible by 3? YES. ($315/3 = 105$). Factor: **3**.
- Is 105 divisible by 3? YES. ($105/3 = 35$). Factor: **3**.
- Is 35 divisible by 3? NO.
- Is 35 divisible by 5? YES. ($35/5 = 7$). Factor: **5**.
- Is 7 divisible by 5? NO.
- Current number is 7 (Prime). Factor: **7**.
Final Factors: **3, 3, 5, 7**.

---

## 3. The "Aha!" Moment
Iterate from $i=2$ to $\sqrt{n}$. While $n$ is divisible by $i$, print $i$ and divide $n$ by $i$. After the loop, if $n > 1$, the remaining $n$ is also a prime factor.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Prime Factorization
 * Efficiency: Time O(sqrt n)
 */
void printPrimeFactors(int n) {
    std::cout << "Prime factors of " << n << ": ";
    
    // Step 1: Handle all 2s
    while (n % 2 == 0) {
        std::cout << 2 << " ";
        n /= 2;
    }
    
    // Step 2: Handle odd numbers from 3 up to sqrt(n)
    for (int i = 3; i * i <= n; i += 2) {
        while (n % i == 0) {
            std::cout << i << " ";
            n /= i;
        }
    }
    
    // Step 3: If n is still > 2, then n is a prime factor
    if (n > 2) {
        std::cout << n;
    }
    
    std::cout << std::endl;
}

int main() {
    printPrimeFactors(315);
    printPrimeFactors(12);
    return 0;
}
```
