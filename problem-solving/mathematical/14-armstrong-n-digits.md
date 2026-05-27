# 14 | Armstrong Number (N Digits)

A general check for Armstrong numbers of any length.

---

## 1. The Objective
An $n$-digit number is an Armstrong number if the sum of its digits raised to the power of $n$ equals the number itself.
- **Example (4 digits):** $1634 = 1^4 + 6^4 + 3^4 + 4^4 = 1 + 1296 + 81 + 256 = 1634$.

---

## 2. Visual Logic
### The Two-Step Process
1. **Count Digits:** Determine the value of $n$ (how many digits).
2. **Calculate Sum:** Iterate through digits and calculate $\text{digit}^n$.

---

## 3. The "Aha!" Moment
This problem combines two previous skills: **Counting Digits** (Problem 09) and **Sum of Digits** logic. You must use `std::pow()` or a custom power function.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <cmath>

/**
 * Strategy: Dynamic Power Calculation
 */
bool isArmstrong(long long n) {
    long long original = n;
    int numDigits = 0;
    
    // Step 1: Count digits
    long long temp = n;
    while (temp > 0) {
        temp /= 10;
        numDigits++;
    }
    
    // Step 2: Sum powers
    long long sum = 0;
    temp = n;
    while (temp > 0) {
        int digit = temp % 10;
        sum += pow(digit, numDigits);
        temp /= 10;
    }
    
    return original == sum;
}

int main() {
    long long num = 1634;
    
    if (isArmstrong(num)) {
        std::cout << num << " is an Armstrong number." << std::endl;
    } else {
        std::cout << num << " is NOT an Armstrong number." << std::endl;
    }
    
    return 0;
}
```
