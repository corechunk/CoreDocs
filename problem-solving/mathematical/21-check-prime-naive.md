# 21 | Check Prime (Naive)

A basic check to see if a number is prime.

---

## 1. The Objective
A **Prime Number** is a natural number greater than 1 that has no positive divisors other than 1 and itself.
- **Example:** $2, 3, 5, 7, 11, \dots$
- **Note:** $1$ is NOT a prime number. $2$ is the only even prime.

---

## 2. Visual Logic
### The "Check Everything" Strategy (n=7)
- Is 7 divisible by 2? (7 % 2 != 0)
- Is 7 divisible by 3? (7 % 3 != 0)
- Is 7 divisible by 4? (7 % 4 != 0)
- Is 7 divisible by 5? (7 % 5 != 0)
- Is 7 divisible by 6? (7 % 6 != 0)
Result: **PRIME**

---

## 3. The "Aha!" Moment
A number is prime if it is not divisible by any number between $2$ and $(n-1)$. This is the simplest way to code it, but it is slow for very large numbers ($O(n)$ complexity).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Naive Iteration
 * Efficiency: Time O(n), Space O(1)
 */
bool isPrimeNaive(int n) {
    if (n <= 1) return false;
    
    for (int i = 2; i < n; i++) {
        if (n % i == 0) {
            return false;
        }
    }
    
    return true;
}

int main() {
    int num = 29;
    
    if (isPrimeNaive(num)) {
        std::cout << num << " is a Prime number." << std::endl;
    } else {
        std::cout << num << " is NOT a Prime number." << std::endl;
    }
    
    return 0;
}
```
