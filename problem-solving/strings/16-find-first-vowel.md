# 16 | Find First Vowel

Identify the first vowel in a string and its position.

---

## 1. The Objective
Given `"skyline"`, return `'i'` at index `2`.

---

## 2. Visual Logic
### The "First Responder" Strategy
Iterate from left to right. The moment you hit a character in `{a, e, i, o, u}`, return it immediately.

---

## 3. The "Aha!" Moment
Linear search allows for an early return. You don't need to check the rest of the string once you find the first match.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Early Return Scan
 */
void findFirstVowel(std::string s) {
    std::string vowels = "aeiouAEIOU";
    
    for (int i = 0; i < s.length(); i++) {
        if (vowels.find(s[i]) != std::string::npos) {
            std::cout << "First vowel: '" << s[i] << "' at index " << i << std::endl;
            return;
        }
    }
    std::cout << "No vowels found." << std::endl;
}

int main() {
    findFirstVowel("python");
    return 0;
}
```
