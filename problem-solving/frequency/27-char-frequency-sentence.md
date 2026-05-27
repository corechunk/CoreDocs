# 27 | Char Frequency in Sentence

Count all alphanumeric characters while ignoring case.

---

## 1. The Objective
Given `"Hello World"`, return `h:1, e:1, l:3, o:2, w:1, r:1, d:1`.

---

## 2. Visual Logic
### The "Normalize and Map" Strategy
1. Convert character to lowercase.
2. If it is `isalnum`: `freq[c]++`.

---

## 3. The "Aha!" Moment
Normalizing data (lowering case) before mapping prevents "L" and "l" from being treated as different entries.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <unordered_map>
#include <cctype>

void charFreq(std::string s) {
    std::unordered_map<char, int> freq;
    for (char c : s) {
        if (std::isalnum(c)) {
            freq[std::tolower(c)]++;
        }
    }
    for (auto const& [c, count] : freq) {
        std::cout << c << ":" << count << " ";
    }
}

int main() {
    charFreq("Frequency Mapping!");
    return 0;
}
```
