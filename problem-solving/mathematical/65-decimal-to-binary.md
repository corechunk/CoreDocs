# 65 | Decimal to Binary

Convert a decimal number to its binary representation.

---

## 1. The Objective
Given `13`, return `1101`.

---

## 2. Visual Logic
### The "Remainder" Method
Divide by 2 repeatedly and keep the remainder.
1. `13 / 2 = 6` (Rem: **1**)
2. `6 / 2 = 3`  (Rem: **0**)
3. `3 / 2 = 1`  (Rem: **1**)
4. `1 / 2 = 0`  (Rem: **1**)
Reading remainders from bottom to top: **1101**.

---

## 3. The "Aha!" Moment
This is the inverse of the extraction loop. Instead of `n % 10`, you use `n % 2`. Since remainders are produced in reverse order, use a string or a stack to flip them back.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <algorithm>

/**
 * Strategy: Repeated Division
 */
std::string decimalToBinary(int n) {
    if (n == 0) return "0";
    
    std::string binary = "";
    while (n > 0) {
        binary += std::to_string(n % 2);
        n /= 2;
    }
    // Flip the string because we collected remainders in reverse
    std::reverse(binary.begin(), binary.end());
    return binary;
}

int main() {
    int num = 13;
    std::cout << num << " in binary is " << decimalToBinary(num) << std::endl;
    return 0;
}
```
