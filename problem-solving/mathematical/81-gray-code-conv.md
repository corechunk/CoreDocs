# 81 | Gray Code Conversion

Convert a binary number to Gray code and vice versa.

---

## 1. The Objective
**Gray Code** is a binary numeral system where two successive values differ in only one bit.
- Binary `2` (10) -> Gray `3` (11).
- Binary `3` (11) -> Gray `2` (10).

---

## 2. Visual Logic
### Binary to Gray
Shift the binary number right by one and XOR it with the original.
`Gray = Binary ^ (Binary >> 1)`

### Gray to Binary
The first bit is the same. Each subsequent binary bit is the XOR of the previous binary bit and the current Gray bit.

---

## 3. The "Aha!" Moment
Gray code is used in hardware (like rotary encoders) to prevent errors during state transitions. The mathematical conversion is a beautiful application of the **XOR** operator.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Bitwise XOR and Shift
 */
int binaryToGray(int n) {
    return n ^ (n >> 1);
}

int grayToBinary(int n) {
    int binary = 0;
    for (; n > 0; n >>= 1) {
        binary ^= n;
    }
    return binary;
}

int main() {
    int b = 4; // 100
    int g = binaryToGray(b);
    std::cout << "Binary 4 (100) -> Gray: " << g << " (" << std::boolalpha << (g == 6) << ")" << std::endl;
    std::cout << "Gray " << g << " -> Binary: " << grayToBinary(g) << std::endl;
    return 0;
}
```
