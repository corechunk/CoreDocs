# 49 | Morse Code Conversion

Convert text to Morse code dots and dashes.

---

## 1. The Objective
Given `"SOS"`, return `"... --- ..."`.

---

## 2. Visual Logic
### The "Lookup Table"
Map each letter to its sequence:
- A: `.-`
- B: `-...`
... and so on.

---

## 3. The "Aha!" Moment
Use an array of 26 strings where the index is `char - 'A'`. This gives you $O(1)$ translation for every character.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <vector>

/**
 * Strategy: Static Mapping
 */
std::string toMorse(std::string s) {
    std::string codes[] = {".-", "-...", "-.-.", "-..", ".", "..-.", "--.", "....", "..", ".---", "-.-", ".-..", "--", "-.", "---", ".--.", "--.-", ".-.", "...", "-", "..-", "...-", ".--", "-..-", "-.--", "--.."};
    std::string res = "";
    
    for (char c : s) {
        if (std::isalpha(c)) {
            res += codes[std::toupper(c) - 'A'] + " ";
        }
    }
    return res;
}

int main() {
    std::cout << "SOS: " << toMorse("SOS") << std::endl;
    return 0;
}
```
