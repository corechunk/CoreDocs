# 29 | GCD (Euclidean Algorithm)

Find the Greatest Common Divisor of two numbers efficiently.

---

## 1. The Objective
Given `a = 48` and `b = 18`, return `6`.

---

## 2. Visual Logic
### The "Subtraction/Remainder" Method
The GCD of two numbers also divides their difference. 
1. `48 % 18 = 12` (The new pair is 18 and 12)
2. `18 % 12 = 6`  (The new pair is 12 and 6)
3. `12 % 6 = 0`   (The new pair is 6 and 0)
Stop! The non-zero number is the GCD: **6**.

---

## 3. The "Aha!" Moment
$\text{GCD}(a, b) = \text{GCD}(b, a \pmod b)$. This is one of the most famous recursive relationships in history. It reduces large numbers to zero incredibly fast.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy A: Iterative Euclidean Algorithm
 * Efficiency: Time O(log(min(a,b)))
 */
int gcdIterative(int a, int b) {
    while (b != 0) {
        a = a % b;
        std::swap(a, b);
    }
    return a;
}

/**
 * Strategy B: Recursive Euclidean Algorithm
 */
int gcdRecursive(int a, int b) {
    if (b == 0) return a;
    return gcdRecursive(b, a % b);
}

int main() {
    int a = 48, b = 18;
    
    std::cout << "GCD of " << a << " and " << b << " (Iterative): " << gcdIterative(a, b) << std::endl;
    std::cout << "GCD of " << a << " and " << b << " (Recursive): " << gcdRecursive(a, b) << std::endl;
    
    return 0;
}
```
