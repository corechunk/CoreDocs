# 45 | Caesar Cipher

Encrypt a string by shifting characters by a fixed number.

---

## 1. The Objective
Given `"ABC"`, `shift=3`, return `"DEF"`.
Given `"XYZ"`, `shift=3`, return `"ABC"` (wraparound).

---

## 2. Visual Logic
### The "Cycle" Strategy
Treat the alphabet as a circle of 26.
1. Find position: `pos = c - 'A'`.
2. Apply shift: `newPos = (pos + shift) % 26`.
3. Back to ASCII: `newChar = newPos + 'A'`.

---

## 3. The "Aha!" Moment
The modulo `% 26` is the magic part—it handles the "wraparound" logic automatically so you don't need `if` statements for 'Z' going to 'A'.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <cctype>

/**
 * Strategy: Modulo Wraparound
 */
std::string caesarCipher(std::string s, int shift) {
    std::string res = "";
    shift %= 26; // Normalize shift
    
    for (char c : s) {
        if (std::isalpha(c)) {
            char base = std::isupper(c) ? 'A' : 'a';
            res += (char)((c - base + shift + 26) % 26 + base);
        } else {
            res += c;
        }
    }
    return res;
}

int main() {
    std::string secret = "Hello, World!";
    std::cout << "Encrypted (Shift 3): " << caesarCipher(secret, 3) << std::endl;
    return 0;
}
```
