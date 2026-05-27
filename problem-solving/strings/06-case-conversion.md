# 06 | Case Conversion (Manual)

Convert a string to purely uppercase or lowercase without `toupper()` or `tolower()`.

---

## 1. The Objective
Transform `"Hello"` into `"HELLO"` or `"hello"` using ASCII arithmetic.

---

## 2. Visual Logic
### The ASCII Offset
- 'A' = 65, 'a' = 97. (Gap: 32)
- If character is between 65-90, it is Uppercase.
- If character is between 97-122, it is Lowercase.

```text
Input: 'G' (71)
To Lower: 71 + 32 = 103 ('g')
```

---

## 3. The "Aha!" Moment
Check the bounds first! If you add 32 to a character that is already lowercase, you will get a special character or symbol. Only apply the offset if the character falls within the target case range.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Boundary Check + Offset
 */
std::string toUpperManual(std::string s) {
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= 'a' && s[i] <= 'z') {
            s[i] = s[i] - 32;
        }
    }
    return s;
}

std::string toLowerManual(std::string s) {
    for (int i = 0; i < s.length(); i++) {
        if (s[i] >= 'A' && s[i] <= 'Z') {
            s[i] = s[i] + 32;
        }
    }
    return s;
}

int main() {
    std::string text = "C++ Logic";
    std::cout << "Upper: " << toUpperManual(text) << std::endl;
    std::cout << "Lower: " << toLowerManual(text) << std::endl;
    return 0;
}
```
