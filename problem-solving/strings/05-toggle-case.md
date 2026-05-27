# 05 | Toggle Case

Switch all uppercase letters to lowercase and vice versa.

---

## 1. The Objective
Given `"AbCd"`, return `"aBcD"`.

---

## 2. Visual Logic
### The "ASCII Distance" Strategy
In the ASCII table, the distance between 'A' (65) and 'a' (97) is exactly **32**.
- To Lower: `char + 32`
- To Upper: `char - 32`

---

## 3. The "Aha!" Moment
You don't need `toupper()` functions. Bit 5 of a character determines its case. Adding or subtracting 32 (or XORing with 32) flips that bit.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Manual ASCII Math
 */
void toggleCase(std::string &s) {
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= 'A' && s[i] <= 'Z') {
            s[i] = s[i] + 32; // To Lower
        } else if (s[i] >= 'a' && s[i] <= 'z') {
            s[i] = s[i] - 32; // To Upper
        }
    }
}

/**
 * Strategy B: Bitwise XOR (Pro Way)
 * 32 is (1 << 5). XORing with 32 flips the case bit.
 */
void toggleCaseBitwise(std::string &s) {
    for (char &c : s) {
        if (std::isalpha(c)) {
            c ^= 32;
        }
    }
}

int main() {
    std::string text = "Hello WORLD";
    toggleCaseBitwise(text);
    std::cout << "Toggled: " << text << std::endl;
    return 0;
}
```
