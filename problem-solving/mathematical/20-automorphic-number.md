# 20 | Automorphic Number

Check if the square of a number ends with the number itself.

---

## 1. The Objective
An **Automorphic Number** is a number whose square ends with the same digits as the number itself.
- **Example:** $25$.
- Square: $25^2 = 625$.
- $625$ ends in $25$. (Automorphic!)
- **Example:** $6$.
- Square: $6^2 = 36$.
- $36$ ends in $6$. (Automorphic!)

---

## 2. Visual Logic
### Tracing 76
1. `76^2 = 5776`
2. Compare the last two digits of `5776` with `76`.
3. How to get the last two digits? Use Modulo $10^2$ (where 2 is the number of digits in 76).
4. `5776 % 100 = 76`.
5. Result: **YES**

---

## 3. The "Aha!" Moment
You need to know how many digits are in the original number $n$. If $n$ has $k$ digits, check if `(square % 10^k) == n`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <cmath>

/**
 * Strategy: Square and Modulo Match
 */
bool isAutomorphic(int n) {
    long long square = 1LL * n * n;
    
    // Step 1: Find number of digits in n
    int temp = n;
    int count = 0;
    while (temp > 0) {
        temp /= 10;
        count++;
    }
    
    // Step 2: Extract last 'count' digits from square
    long long divisor = pow(10, count);
    
    return (square % divisor) == n;
}

int main() {
    int num = 76;
    
    if (isAutomorphic(num)) {
        std::cout << num << " is an Automorphic number." << std::endl;
    } else {
        std::cout << num << " is NOT an Automorphic number." << std::endl;
    }
    
    return 0;
}
```
