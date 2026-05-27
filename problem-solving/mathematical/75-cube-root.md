# 75 | Cube Root

Calculate the cube root of a number.

---

## 1. The Objective
Given `125`, return `5`. Given `27`, return `3`.

---

## 2. Visual Logic
### The "Binary Search" Strategy (Floats)
Unlike square roots, cube roots can be calculated for negative numbers.
Range for searching: $[-n, n]$ or $[-10^9, 10^9]$.

---

## 3. The "Aha!" Moment
For any number $x$, if $mid^3 < x$, the root is higher. If $mid^3 > x$, the root is lower.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Binary Search on Floats
 */
double cubeRoot(double n) {
    double low, high;
    if (n >= 0) {
        low = 0;
        high = std::max(1.0, n);
    } else {
        low = std::min(-1.0, n);
        high = 0;
    }
    
    double mid;
    for (int i = 0; i < 100; i++) { // 100 iterations for max precision
        mid = (low + high) / 2.0;
        if (mid * mid * mid < n) low = mid;
        else high = mid;
    }
    return mid;
}

int main() {
    std::cout << "Cube root of 125: " << cubeRoot(125) << std::endl;
    std::cout << "Cube root of -8: " << cubeRoot(-8) << std::endl;
    return 0;
}
```
