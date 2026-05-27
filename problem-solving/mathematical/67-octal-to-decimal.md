# 67 | Octal to Decimal

Convert a base-8 number to base-10.

---

## 1. The Objective
Given `41`, return `33`.

---

## 2. Visual Logic
### The "Power of 8" Weighting
`4 1`
- `4 * 8^1 = 32`
- `1 * 8^0 = 1`
**Sum:** $32 + 1 = 33$.

---

## 3. The "Aha!" Moment
Same logic as Binary to Decimal (Problem 64), but the base is `8`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <cmath>

/**
 * Strategy: Positional Weighting (Base 8)
 */
long long octalToDecimal(std::string octal) {
    long long decimal = 0;
    int p = 0;
    for (int i = octal.length() - 1; i >= 0; i--) {
        int digit = octal[i] - '0';
        decimal += digit * pow(8, p);
        p++;
    }
    return decimal;
}

int main() {
    std::string o = "41";
    std::cout << o << " in decimal is " << octalToDecimal(o) << std::endl;
    return 0;
}
```
