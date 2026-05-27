# 09 | Count Digits

Count how many digits are in a given number.

---

## 1. The Objective
Given `12345`, return `5`.

---

## 2. Visual Logic
### The "Peeling" Method
Divide the number by 10 repeatedly. Each division "peels off" the last digit.
1. `12345 / 10 = 1234` (Count: 1)
2. `1234 / 10 = 123` (Count: 2)
3. `123 / 10 = 12` (Count: 3)
4. `12 / 10 = 1` (Count: 4)
5. `1 / 10 = 0` (Count: 5)
6. Stop when number is 0.

---

## 3. The "Aha!" Moment
- **Iterative:** Use a `while` loop to divide by 10 until you reach zero.
- **Logarithmic:** $\text{Count} = \lfloor \log_{10}(n) \rfloor + 1$. This is the fastest mathematical way.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <cmath> // for std::log10

/**
 * Strategy A: Iterative (The Loop)
 */
int countDigitsIterative(long long n) {
    if (n == 0) return 1;
    if (n < 0) n = -n; // Handle negative numbers
    
    int count = 0;
    while (n > 0) {
        n /= 10;
        count++;
    }
    return count;
}

/**
 * Strategy B: Logarithmic (The Math Way)
 * Note: Fast but doesn't handle 0 well (log10 of 0 is undefined)
 */
int countDigitsMath(long long n) {
    if (n == 0) return 1;
    if (n < 0) n = -n;
    return floor(log10(n)) + 1;
}

int main() {
    long long num = 9876543210;
    
    std::cout << "Digits in " << num << " (Iterative): " << countDigitsIterative(num) << std::endl;
    std::cout << "Digits in " << num << " (Math): " << countDigitsMath(num) << std::endl;
    
    return 0;
}
```
