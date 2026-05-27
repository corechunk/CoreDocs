# 32 | Run-Length Decoding

Reconstruct a string from its compressed RLE format.

---

## 1. The Objective
Given `"a3b2c4"`, return `"aaabbcccc"`.

---

## 2. Visual Logic
### The "Multiplier" Strategy
1. Read the character: `'a'`.
2. Read the following number: `3`.
3. Append `'a'` to the result `3` times.
4. Move to next character.

---

## 3. The "Aha!" Moment
The "number" part might be more than one digit (e.g., `a12`). You must parse the number fully until you hit the next letter.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <cctype>

/**
 * Strategy: Multi-digit parsing
 */
std::string decodeRLE(std::string s) {
    std::string res = "";
    for (int i = 0; i < s.length(); i++) {
        char c = s[i];
        
        // Find the number following the char
        std::string numStr = "";
        while (i + 1 < s.length() && std::isdigit(s[i + 1])) {
            numStr += s[i + 1];
            i++;
        }
        
        int count = std::stoi(numStr);
        for (int j = 0; j < count; j++) res += c;
    }
    return res;
}

int main() {
    std::string s = "a10b2c3";
    std::cout << "Decoded: " << decodeRLE(s) << std::endl;
    return 0;
}
```
