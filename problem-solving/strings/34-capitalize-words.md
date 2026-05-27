# 34 | Capitalize Words

Transform every word in a sentence to start with an uppercase letter.

---

## 1. The Objective
Given `"hello world from c++"`, return `"Hello World From C++"`.

---

## 2. Visual Logic
### The "After-Space" Strategy
The first character is always capitalized.
Any character that follows a space is capitalized.

---

## 3. The "Aha!" Moment
Use a boolean flag `newWord = true`. When you see a character, if `newWord` is true, capitalize it and set `newWord = false`. When you see a space, set `newWord = true`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <cctype>

/**
 * Strategy: State-based capitalization
 */
void capitalizeWords(std::string &s) {
    bool nextUpper = true;
    for (char &c : s) {
        if (std::isspace(c)) {
            nextUpper = true;
        } else if (nextUpper && std::isalpha(c)) {
            c = std::toupper(c);
            nextUpper = false;
        } else {
            c = std::tolower(c); // Ensure rest is lower
            nextUpper = false;
        }
    }
}

int main() {
    std::string s = "tHis Is a tEST";
    capitalizeWords(s);
    std::cout << "Result: " << s << std::endl;
    return 0;
}
```
