# 66 | Decimal to Octal

Convert a base-10 number to base-8.

---

## 1. The Objective
Given `33`, return `41`.
Octal uses digits 0-7.

---

## 2. Visual Logic
### The "Divide by 8" Method
1. `33 / 8 = 4` (Rem: **1**)
2. `4 / 8 = 0`  (Rem: **4**)
Octal: **41**.

---

## 3. The "Aha!" Moment
This is the same logic as Decimal to Binary (Problem 65), but the divisor is `8`. Base conversion is a universal pattern: replace the divisor with your target base.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <algorithm>

/**
 * Strategy: Repeated Division by 8
 */
std::string decimalToOctal(int n) {
    if (n == 0) return "0";
    
    std::string octal = "";
    while (n > 0) {
        octal += std::to_string(n % 8);
        n /= 8;
    }
    std::reverse(octal.begin(), octal.end());
    return octal;
}

int main() {
    int num = 33;
    std::cout << num << " in octal is " << decimalToOctal(num) << std::endl;
    return 0;
}
```
