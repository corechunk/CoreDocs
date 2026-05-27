# 50 | Vigenère Cipher

Encrypt text using a keyword to shift letters.

---

## 1. The Objective
Unlike Caesar cipher (fixed shift), Vigenère uses a word.
- Text: `ATTACK`
- Key: `LEMON`
- Each letter in ATTACK is shifted by the corresponding letter in LEMON (repeated).

---

## 2. Visual Logic
### The "Variable Shift"
1. 'A' + 'L' (shift 11) $\to$ 'L'
2. 'T' + 'E' (shift 4) $\to$ 'X'
3. 'T' + 'M' (shift 12) $\to$ 'F'

---

## 3. The "Aha!" Moment
The key "loops" back to the start if the text is longer than the key. Use `keyIndex % keyLength` to achieve this cycle.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Cyclic key shifting
 */
std::string vigenereEncrypt(std::string text, std::string key) {
    std::string res = "";
    int j = 0; // Key index
    
    for (int i = 0; i < text.length(); i++) {
        char c = text[i];
        if (std::isalpha(c)) {
            char base = std::isupper(c) ? 'A' : 'a';
            int shift = std::toupper(key[j % key.length()]) - 'A';
            res += (char)((c - base + shift) % 26 + base);
            j++;
        } else {
            res += c;
        }
    }
    return res;
}

int main() {
    std::cout << "Encrypted: " << vigenereEncrypt("ATTACKATDAWN", "LEMON") << std::endl;
    return 0;
}
```
