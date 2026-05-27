# 17 | Harshad Number

Check if a number is divisible by the sum of its digits.

---

## 1. The Objective
A **Harshad Number** (or Niven number) is an integer that is divisible by the sum of its digits.
- **Example:** $18$.
- Sum of digits: $1 + 8 = 9$.
- $18 / 9 = 2$ (Divisible! 18 is a Harshad number).

---

## 2. Visual Logic
### Tracing 156
1. `Sum = 1 + 5 + 6 = 12`
2. `Check: 156 % 12`
3. `156 / 12 = 13` (Remainder 0)
4. Result: **YES**

---

## 3. The "Aha!" Moment
This is a direct application of the **Sum of Digits** logic (Problem 10). Calculate the sum first, then perform one final modulo check.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Sum of Digits + Modulo Check
 */
bool isHarshad(int n) {
    int sum = 0;
    int temp = n;
    
    while (temp > 0) {
        sum += (temp % 10);
        temp /= 10;
    }
    
    return n % sum == 0;
}

int main() {
    int num = 18;
    
    if (isHarshad(num)) {
        std::cout << num << " is a Harshad number." << std::endl;
    } else {
        std::cout << num << " is NOT a Harshad number." << std::endl;
    }
    
    return 0;
}
```
