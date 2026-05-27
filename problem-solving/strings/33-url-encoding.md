# 33 | URL Encoding

Replace spaces with `%20`.

---

## 1. The Objective
Given `"google search"`, return `"google%20search"`.

---

## 2. Visual Logic
### The "Substitution" Strategy
1. Find all spaces.
2. If using a new string: Just append `%20` instead of `' '`.
3. If in-place: You need to expand the array from the back to make room.

---

## 3. The "Aha!" Moment
A space is 1 char, but `%20` is 3 chars. You need 2 extra spaces for every space found.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Target string construction
 */
std::string urlEncode(std::string s) {
    std::string res = "";
    for (char c : s) {
        if (c == ' ') res += "%20";
        else res += c;
    }
    return res;
}

int main() {
    std::string s = "hello world search";
    std::cout << "Encoded: " << urlEncode(s) << std::endl;
    return 0;
}
```
