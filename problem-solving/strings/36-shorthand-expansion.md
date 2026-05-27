# 36 | Shorthand Expansion

Expand shorthand ranges like `a-z` or `1-9` into full sequences.

---

## 1. The Objective
Given `"a-e1-3"`, return `"abcde123"`.

---

## 2. Visual Logic
### The "Bridge" Strategy
1. Scan for the `-` character.
2. Identify the character before (`start`) and after (`end`).
3. Loop from `start` to `end` and append all intermediate characters.

---

## 3. The "Aha!" Moment
Characters are sequential in ASCII. A loop `for (char c = start; c <= end; c++)` works perfectly for both letters and numbers.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Range expansion loop
 */
std::string expandShorthand(std::string s) {
    std::string res = "";
    for (int i = 0; i < s.length(); i++) {
        if (s[i] == '-' && i > 0 && i < s.length() - 1) {
            // Found a bridge!
            for (char c = s[i - 1] + 1; c < s[i + 1]; c++) {
                res += c;
            }
        } else {
            res += s[i];
        }
    }
    return res;
}

int main() {
    std::cout << "Expand a-z: " << expandShorthand("a-z") << std::endl;
    std::cout << "Expand 0-9: " << expandShorthand("0-9") << std::endl;
    return 0;
}
```
