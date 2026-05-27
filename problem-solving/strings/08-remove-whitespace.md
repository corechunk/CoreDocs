# 08 | Remove Whitespace

Remove all spaces from a string.

---

## 1. The Objective
Given `" H e l l o "`, return `"Hello"`.

---

## 2. Visual Logic
### The "New Container" Strategy
1. Create an empty result string.
2. Iterate through input.
3. If char is NOT `' '`, push it into result.

---

## 3. The "Aha!" Moment
The `isspace()` function in C++ is better than checking for `' '` because it also catches tabs (`\t`) and newlines (`\n`).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <cctype>

/**
 * Strategy: Filter and Rebuild
 */
std::string removeSpaces(std::string s) {
    std::string result = "";
    for (char c : s) {
        if (!std::isspace(c)) {
            result += c;
        }
    }
    return result;
}

int main() {
    std::string text = "  A B C  D  ";
    std::cout << "Clean: [" << removeSpaces(text) << "]" << std::endl;
    return 0;
}
```
