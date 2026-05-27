# 10 | Sum of Digits

Calculate the sum of all digits in a given number.

---

## 1. The Objective
Given `123`, return $1 + 2 + 3 = 6$.

---

## 2. Visual Logic
### The "Extract and Peel" Method
1. `123 % 10 = 3` (Remainder is the last digit)
2. `Sum = 0 + 3 = 3`
3. `123 / 10 = 12` (Remove the last digit)
---
4. `12 % 10 = 2`
5. `Sum = 3 + 2 = 5`
6. `12 / 10 = 1`
---
7. `1 % 10 = 1`
8. `Sum = 5 + 1 = 6`
9. `1 / 10 = 0` (Stop)

---

## 3. The "Aha!" Moment
Use Modulo (`%`) to **extract** the digit and Division (`/`) to **discard** it. This loop is the foundation for almost all digit-based problems.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy A: Iterative
 */
int sumOfDigits(long long n) {
    if (n < 0) n = -n;
    
    int sum = 0;
    while (n > 0) {
        sum += (n % 10);
        n /= 10;
    }
    return sum;
}

/**
 * Strategy B: Recursive
 */
int sumOfDigitsRecursive(long long n) {
    if (n == 0) return 0;
    return (n % 10) + sumOfDigitsRecursive(n / 10);
}

int main() {
    long long num = 12345;
    
    std::cout << "Sum of digits in " << num << ": " << sumOfDigits(num) << std::endl;
    
    return 0;
}
```
