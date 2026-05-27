# 30 | LCM Logic

Find the Least Common Multiple of two numbers.

---

## 1. The Objective
Given `a = 12` and `b = 18`, return `36`.

---

## 2. Visual Logic
### The "Overlap" Relationship
The product of two numbers is equal to the product of their GCD and LCM.
$a \times b = \text{GCD}(a, b) \times \text{LCM}(a, b)$

- $12 \times 18 = 216$
- $\text{GCD}(12, 18) = 6$
- $\text{LCM} = 216 / 6 = 36$.

---

## 3. The "Aha!" Moment
Don't try to find the LCM by looping. Find the GCD first (which is fast), then use the formula:
$\text{LCM}(a, b) = \frac{|a \times b|}{\text{GCD}(a, b)}$

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Helper: GCD
 */
int gcd(int a, int b) {
    while (b != 0) {
        a %= b;
        std::swap(a, b);
    }
    return a;
}

/**
 * Strategy: Formula-based LCM
 * Efficiency: Time O(log(min(a,b)))
 */
long long lcm(int a, int b) {
    if (a == 0 || b == 0) return 0;
    
    // Use (a/gcd)*b to prevent overflow during multiplication
    return (1LL * std::abs(a) / gcd(a, b)) * std::abs(b);
}

int main() {
    int x = 12, y = 18;
    std::cout << "LCM of " << x << " and " << y << " is: " << lcm(x, y) << std::endl;
    return 0;
}
```
