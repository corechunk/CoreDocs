# 69 | Hexadecimal to Decimal

Convert a base-16 string to base-10.

---

## 1. The Objective
Given `1C2`, return `450`.

---

## 2. Visual Logic
### The "Char-to-Val" Weighting
`1 C 2`
- `1 * 16^2 = 256`
- `12 * 16^1 = 192`
- `2 * 16^0 = 2`
**Sum:** $256 + 192 + 2 = 450$.

---

## 3. The "Aha!" Moment
You must convert characters like 'A' or 'c' back into their integer values (10 or 12).
Check if char is digit: `c - '0'`.
Check if char is letter: `toupper(c) - 'A' + 10`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <cmath>

/**
 * Strategy: Char-Value conversion + Weighting
 */
long long hexToDecimal(std::string hex) {
    long long decimal = 0;
    int p = 0;
    
    for (int i = hex.length() - 1; i >= 0; i--) {
        char c = std::toupper(hex[i]);
        int val;
        if (c >= '0' && c <= '9') val = c - '0';
        else val = c - 'A' + 10;
        
        decimal += val * pow(16, p);
        p++;
    }
    return decimal;
}

int main() {
    std::string h = "1C2";
    std::cout << h << " in decimal is " << hexToDecimal(h) << std::endl;
    return 0;
}
```
