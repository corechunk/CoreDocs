# 70 | Any Base to Any Base

A universal base converter.

---

## 1. The Objective
Given `1101` in base 2, convert it to base 16.

---

## 2. Visual Logic
### The "Decimal Bridge" Strategy
Converting directly between arbitrary bases (like 3 to 7) is hard. It's easier to use base 10 as a middle-man.
`[Base A] -> [Base 10] -> [Base B]`

---

## 3. The "Aha!" Moment
Reuse the logic from previous problems. Create a function `toDecimal(num, fromBase)` and a function `fromDecimal(decimal, toBase)`. Combine them for the final result.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <algorithm>
#include <cmath>

/**
 * Universal Base Converter
 */
long long toDecimal(std::string num, int base) {
    long long res = 0;
    int p = 0;
    for (int i = num.length() - 1; i >= 0; i--) {
        char c = std::toupper(num[i]);
        int val = (c >= '0' && c <= '9') ? (c - '0') : (c - 'A' + 10);
        res += val * pow(base, p++);
    }
    return res;
}

std::string fromDecimal(long long n, int base) {
    std::string map = "0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    std::string res = "";
    while (n > 0) {
        res += map[n % base];
        n /= base;
    }
    std::reverse(res.begin(), res.end());
    return res;
}

int main() {
    std::string num = "1101"; // 13 decimal
    int from = 2, to = 16;
    
    long long dec = toDecimal(num, from);
    std::string result = fromDecimal(dec, to);
    
    std::cout << num << " (base " << from << ") = " << result << " (base " << to << ")" << std::endl;
    return 0;
}
```
