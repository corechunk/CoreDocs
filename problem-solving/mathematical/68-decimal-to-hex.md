# 68 | Decimal to Hexadecimal

Convert a base-10 number to base-16.

---

## 1. The Objective
Given `450`, return `1C2`.
Hex uses 0-9 and A-F.

---

## 2. Visual Logic
### The "Alpha Remainder" Method
1. `450 / 16 = 28` (Rem: **2**)
2. `28 / 16 = 1`  (Rem: **12**) -> **C**
3. `1 / 16 = 0`   (Rem: **1**)
Hex: **1C2**.

---

## 3. The "Aha!" Moment
When the remainder is $> 9$, you must map it to a character: $10 \to A, 11 \to B \dots 15 \to F$. A lookup string `"0123456789ABCDEF"` is the easiest way.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <algorithm>

/**
 * Strategy: Remainder Mapping
 */
std::string decimalToHex(int n) {
    if (n == 0) return "0";
    
    std::string hexMap = "0123456789ABCDEF";
    std::string hex = "";
    
    while (n > 0) {
        int rem = n % 16;
        hex += hexMap[rem];
        n /= 16;
    }
    std::reverse(hex.begin(), hex.end());
    return hex;
}

int main() {
    int num = 450;
    std::cout << num << " in hex is " << decimalToHex(num) << std::endl;
    return 0;
}
```
