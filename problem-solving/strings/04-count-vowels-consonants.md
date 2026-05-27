# 04 | Count Vowels & Consonants

Determine the distribution of letters in a string.

---

## 1. The Objective
Count how many vowels (a, e, i, o, u) and consonants are in a given string.

---

## 2. Visual Logic
### The "Filter" Strategy
Iterate through every character:
1. Is it a letter? (Ignore spaces/numbers).
2. If YES: Is it in the set `{a, e, i, o, u}`?
   - YES $\to$ Vowel++
   - NO $\to$ Consonant++

---

## 3. The "Aha!" Moment
Characters are just numbers (ASCII). You should convert everything to lowercase (or uppercase) before checking to avoid double checks like `if (c == 'a' || c == 'A')`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <cctype> // for tolower and isalpha

/**
 * Strategy: Linear scan with ASCII filter
 */
void countStats(std::string s) {
    int vowels = 0, consonants = 0;
    
    for (char c : s) {
        if (std::isalpha(c)) { // Check if it's a letter
            char lower = std::tolower(c);
            if (lower == 'a' || lower == 'e' || lower == 'i' || lower == 'o' || lower == 'u') {
                vowels++;
            } else {
                consonants++;
            }
        }
    }
    
    std::cout << "Vowels: " << vowels << std::endl;
    std::cout << "Consonants: " << consonants << std::endl;
}

int main() {
    std::string text = "Programming is Fun!";
    countStats(text);
    return 0;
}
```
