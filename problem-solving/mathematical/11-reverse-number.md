# 11 | Reverse a Number

Reverse the digits of a given integer.

---

## 1. The Objective
Given `1234`, return `4321`.

---

## 2. Visual Logic
### The "Build-Up" Method
1. `Number: 1234, Reverse: 0`
2. `Extract last digit (1234 % 10 = 4)`
3. `Push into reverse (0 * 10 + 4 = 4)`
4. `Discard last digit (1234 / 10 = 123)`
---
5. `Extract (123 % 10 = 3)`
6. `Push (4 * 10 + 3 = 43)`
7. `Discard (123 / 10 = 12)`
---
... and so on.

---

## 3. The "Aha!" Moment
To "shift" a number to the left, multiply by 10. To "shift" to the right, divide by 10. By combining these, you can move digits from one number to another in reverse order.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy A: Iterative Reversal
 * Efficiency: Time O(log N), Space O(1)
 */
long long reverseNumber(long long n) {
    long long reversed = 0;
    while (n != 0) {
        int digit = n % 10;
        reversed = (reversed * 10) + digit;
        n /= 10;
    }
    return reversed;
}

int main() {
    long long num = 12345;
    
    std::cout << "Original: " << num << std::endl;
    std::cout << "Reversed: " << reverseNumber(num) << std::endl;
    
    return 0;
}
```
