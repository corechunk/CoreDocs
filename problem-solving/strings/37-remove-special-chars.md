# 37 | Remove Special Characters

Keep only alphanumeric characters (a-z, A-Z, 0-9).

---

## 1. The Objective
Given `"Hello, World! 123"`, return `"HelloWorld123"`.

---

## 2. Visual Logic
### The "Whitelist" Filter
1. Create empty result.
2. For each character `c`:
   - If `isalnum(c)` is true: Append to result.

---

## 3. The "Aha!" Moment
The `<cctype>` library provides `isalnum()`, which is cleaner than checking four different ASCII ranges manually.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <cctype>

/**
 * Strategy: Alpha-Numeric Filtering
 */
std::string cleanString(std::string s) {
    std::string res = "";
    for (char c : s) {
        if (std::isalnum(c)) {
            res += c;
        }
    }
    return res;
}

int main() {
    std::string s = "user_name#123@host";
    std::cout << "Cleaned: " << cleanString(s) << std::endl;
    return 0;
}
```
