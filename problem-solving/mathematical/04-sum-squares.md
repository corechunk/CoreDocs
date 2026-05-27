# 04 | Sum of Squares

Calculate the sum: $1^2 + 2^2 + 3^2 + \dots + n^2$.

---

## 1. The Objective
Given $n$, find the sum of squares of the first $n$ natural numbers.

---

## 2. Visual Logic
### Tracing (n=3)
$1^2 = 1$
$2^2 = 4$
$3^2 = 9$
Sum = $1 + 4 + 9 = 14$

---

## 3. The "Aha!" Moment
- **The Loop:** Just like the natural sum, but square the number before adding.
- **The Formula:** There is a specific mathematical formula for this:
  $Sum = \frac{n(n+1)(2n+1)}{6}$

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy A: Iterative
 * Efficiency: Time O(n)
 */
long long sumSquaresIterative(int n) {
    long long sum = 0;
    for (int i = 1; i <= n; i++) {
        sum += (1LL * i * i);
    }
    return sum;
}

/**
 * Strategy B: Mathematical Formula
 * Efficiency: Time O(1)
 */
long long sumSquaresFormula(int n) {
    return (1LL * n * (n + 1) * (2 * n + 1)) / 6;
}

int main() {
    int n = 10;
    
    std::cout << "Sum of squares to " << n << " (Iterative): " << sumSquaresIterative(n) << std::endl;
    std::cout << "Sum of squares to " << n << " (Formula): " << sumSquaresFormula(n) << std::endl;
    
    return 0;
}
```
