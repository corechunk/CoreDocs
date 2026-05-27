# 39 | Semi-Prime

Check if a number is the product of exactly two prime numbers.

---

## 1. The Objective
A **Semi-prime** is a natural number that is the product of two prime numbers (not necessarily distinct).
- **Example:** $6 = 2 \times 3$ (Semi-prime)
- **Example:** $9 = 3 \times 3$ (Semi-prime)
- **Example:** $12 = 2 \times 2 \times 3$ (NOT semi-prime, has 3 factors)

---

## 2. Visual Logic
### The Factor Count Strategy
1. Find all prime factors of $n$.
2. Keep a counter of how many factors you find.
3. If the total count is exactly 2, it's a semi-prime.

---

## 3. The "Aha!" Moment
Modify the **Prime Factors** loop (Problem 25). Instead of printing them, just count them.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Exact Factor Count
 */
bool isSemiprime(int n) {
    int count = 0;
    int temp = n;
    
    for (int i = 2; i * i <= temp && count < 2; i++) {
        while (temp % i == 0) {
            temp /= i;
            count++; // Found a prime factor
        }
    }
    
    // If temp > 1, the remaining part is a prime factor
    if (temp > 1) count++;
    
    return count == 2;
}

int main() {
    int num = 15; // 3 * 5
    if (isSemiprime(num)) std::cout << num << " is a Semi-prime." << std::endl;
    else std::cout << num << " is NOT a Semi-prime." << std::endl;
    return 0;
}
```
