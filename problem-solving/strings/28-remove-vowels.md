# 28 | Remove Vowels

Strip all vowels from a string.

---

## 1. The Objective
Given `"Beautiful"`, return `"Btfl"`.

---

## 2. Visual Logic
### The "Blacklist" Strategy
Create a string or set of vowels: `"aeiouAEIOU"`.
If the current character is **NOT** in that set, keep it.

---

## 3. The "Aha!" Moment
Use `string::find` on your blacklist. If it returns `npos`, it means the character is safe (a consonant or symbol).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Character Filtering
 */
std::string stripVowels(std::string s) {
    std::string res = "";
    std::string vowels = "aeiouAEIOU";
    
    for (char c : s) {
        if (vowels.find(c) == std::string::npos) {
            res += c;
        }
    }
    return res;
}

int main() {
    std::cout << "Result: " << stripVowels("Mathematical Logic") << std::endl;
    return 0;
}
```
