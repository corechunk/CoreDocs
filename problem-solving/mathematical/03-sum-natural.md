# 03 | Sum of Natural Numbers

Calculate the sum of the first $n$ positive integers.

---

## 1. The Objective
Find the sum: $1 + 2 + 3 + \dots + n$.

---

## 2. Visual Logic
### The "Gauß" Visual (n=10)
Imagine you have numbers 1 to 10. Pair the first and last:
- $1 + 10 = 11$
- $2 + 9 = 11$
- $3 + 8 = 11$
- $4 + 7 = 11$
- $5 + 6 = 11$

There are $10/2 = 5$ pairs of 11. 
Total Sum = $5 \times 11 = 55$.

---

## 3. The "Aha!" Moment
- **The Formula:** Carl Friedrich Gauß discovered that the sum is always $\frac{n(n+1)}{2}$. 
- **The Loop:** If you don't use the formula, you just accumulate values in a loop.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy A: Iterative (The Loop)
 * Efficiency: Time O(n)
 */
long long sumIterative(int n) {
    long long sum = 0;
    for (int i = 1; i <= n; i++) {
        sum += i;
    }
    return sum;
}

/**
 * Strategy B: Mathematical (The Formula)
 * Efficiency: Time O(1) - The "Pro" Way
 */
long long sumFormula(int n) {
    return (1LL * n * (n + 1)) / 2;
}

int main() {
    int n = 100;
    
    std::cout << "Sum up to " << n << " (Iterative): " << sumIterative(n) << std::endl;
    std::cout << "Sum up to " << n << " (Formula): " << sumFormula(n) << std::endl;
    
    return 0;
}
```
