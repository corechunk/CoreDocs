# 15 | Digit-Only Check

Verify if a string consists only of numbers.

---

## 1. The Objective
Given `"12345"`, return `true`. Given `"12a45"`, return `false`.

---

## 2. Visual Logic
### The "One Bad Apple" Rule
Assume the string is perfect. Check every character. If even one is not a digit, the whole string fails.

---

## 3. The "Aha!" Moment
A simple loop with `isdigit()`. Empty strings should usually return `false` in this logic.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <cctype>

/**
 * Strategy: Early Exit on non-digit
 */
bool isNumeric(std::string s) {
    if (s.empty()) return false;
    
    for (char c : s) {
        if (!std::isdigit(c)) {
            return false;
        }
    }
    return true;
}

int main() {
    std::cout << "Is '123' numeric? " << (isNumeric("123") ? "Yes" : "No") << std::endl;
    std::cout << "Is '1a3' numeric? " << (isNumeric("1a3") ? "Yes" : "No") << std::endl;
    return 0;
}
```
