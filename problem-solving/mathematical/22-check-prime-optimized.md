# 22 | Check Prime (Optimized)

The efficient way to check for primality.

---

## 1. The Objective
Check if a number is prime using the $O(\sqrt{n})$ approach.

---

## 2. Visual Logic
### The "Mirror" Property
If a number $n$ has a divisor greater than $\sqrt{n}$, it **must** have a corresponding divisor smaller than $\sqrt{n}$.
- **Example:** $n = 36$. $\sqrt{36} = 6$.
- Divisors: $2 \times 18, 3 \times 12, 4 \times 9, 6 \times 6$.
- See how the pairs "flip" after 6?
- $9 \times 4, 12 \times 3, 18 \times 2$.

**Conclusion:** If we don't find a divisor by the time we reach $\sqrt{n}$, we never will.

---

## 3. The "Aha!" Moment
1.  Handle small cases (2 and 3) immediately.
2.  If the number is divisible by 2 or 3, it's not prime.
3.  Check divisors from 5 up to $\sqrt{n}$ in steps of 6 ($i$ and $i+2$). This skips all multiples of 2 and 3!

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Optimized O(sqrt n)
 * Efficiency: Time O(sqrt n), Space O(1)
 */
bool isPrimeOptimized(int n) {
    if (n <= 1) return false;
    if (n <= 3) return true;
    
    // Skip multiples of 2 and 3
    if (n % 2 == 0 || n % 3 == 0) return false;
    
    // Check from 5 to sqrt(n)
    // All primes are of the form 6k +/- 1
    for (int i = 5; i * i <= n; i = i + 6) {
        if (n % i == 0 || n % (i + 2) == 0) {
            return false;
        }
    }
    
    return true;
}

int main() {
    long long num = 1000000007; // A large prime
    
    if (isPrimeOptimized(num)) {
        std::cout << num << " is Prime." << std::endl;
    } else {
        std::cout << num << " is NOT Prime." << std::endl;
    }
    
    return 0;
}
```
