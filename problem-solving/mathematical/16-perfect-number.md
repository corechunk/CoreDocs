# 16 | Perfect Number

Check if a number is equal to the sum of its proper divisors.

---

## 1. The Objective
A **Perfect Number** is a positive integer that is equal to the sum of its positive divisors, excluding the number itself.
- **Example:** $6$ has divisors $1, 2, 3$.
- $1 + 2 + 3 = 6$. (Perfect!)
- **Example:** $28$ has divisors $1, 2, 4, 7, 14$.
- $1 + 2 + 4 + 7 + 14 = 28$. (Perfect!)

---

## 2. Visual Logic
### Divisor Search (n=28)
- $28 / 1 = 28$ (Divisor: 1)
- $28 / 2 = 14$ (Divisor: 2)
- $28 / 3 =$ NO
- $28 / 4 = 7$ (Divisor: 4)
- $28 / 5 =$ NO
- ...
- Summing: $1 + 2 + 4 + 7 + 14 = 28$.

---

## 3. The "Aha!" Moment
Iterate from 1 up to $n/2$. If $n \% i == 0$, then $i$ is a proper divisor. Sum these up and compare with the original $n$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Iterative Divisor Summing
 * Efficiency: Time O(n), Space O(1)
 */
bool isPerfect(int n) {
    if (n <= 1) return false;
    
    int sum = 0;
    for (int i = 1; i <= n / 2; i++) {
        if (n % i == 0) {
            sum += i;
        }
    }
    
    return sum == n;
}

int main() {
    int num = 28;
    
    if (isPerfect(num)) {
        std::cout << num << " is a Perfect number." << std::endl;
    } else {
        std::cout << num << " is NOT a Perfect number." << std::endl;
    }
    
    return 0;
}
```
