# 64 | Binary to Decimal

Convert a binary string/number to its decimal equivalent.

---

## 1. The Objective
Given `1101_2`, return `13`.

---

## 2. Visual Logic
### The "Power of 2" Weighting
Each digit has a weight: $2^p$ where $p$ is the position from the right (starting at 0).
`1 1 0 1`
- `1 * 2^3 = 8`
- `1 * 2^2 = 4`
- `0 * 2^1 = 0`
- `1 * 2^0 = 1`
**Sum:** $8 + 4 + 0 + 1 = 13$.

---

## 3. The "Aha!" Moment
As you iterate through the digits from right to left, multiply the digit by the current `base_value` (1, 2, 4, 8...), then double the `base_value` for the next step.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Positional Weighting
 */
long long binaryToDecimal(std::string binary) {
    long long decimal = 0;
    long long base = 1; // 2^0
    
    // Iterate from right to left
    for (int i = binary.length() - 1; i >= 0; i--) {
        if (binary[i] == '1') {
            decimal += base;
        }
        base *= 2;
    }
    return decimal;
}

int main() {
    std::string b = "11010";
    std::cout << b << " in decimal is " << binaryToDecimal(b) << std::endl;
    return 0;
}
```
