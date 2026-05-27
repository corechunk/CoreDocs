# 22 | Pangram Check

Check if a string contains every letter of the alphabet (a-z).

---

## 1. The Objective
Given `"The quick brown fox jumps over the lazy dog"`, return `true`.

---

## 2. Visual Logic
### The "Checklist" Strategy
1. Create a boolean array `checklist[26]` for 'a' through 'z'.
2. Iterate through the string.
3. If character is a letter, mark it on the checklist.
4. If all 26 boxes are checked, it's a pangram.

---

## 3. The "Aha!" Moment
Pangrams don't care about numbers or symbols. They only care about the **existence** of all 26 distinct letters.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <vector>
#include <cctype>

/**
 * Strategy: Boolean Checklist
 */
bool isPangram(std::string s) {
    std::vector<bool> seen(26, false);
    int uniqueCount = 0;
    
    for (char c : s) {
        if (std::isalpha(c)) {
            int index = std::tolower(c) - 'a';
            if (!seen[index]) {
                seen[index] = true;
                uniqueCount++;
            }
        }
    }
    return uniqueCount == 26;
}

int main() {
    std::string s = "Pack my box with five dozen liquor jugs.";
    std::cout << "Is Pangram? " << (isPangram(s) ? "Yes" : "No") << std::endl;
    return 0;
}
```
