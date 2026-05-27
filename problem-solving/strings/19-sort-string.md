# 19 | Sort String Characters

Arrange the characters of a string in alphabetical order.

---

## 1. The Objective
Given `"dcba"`, return `"abcd"`.

---

## 2. Visual Logic
### The "Bubble" or "Selection" Strategy
1. Compare `s[i]` and `s[j]`.
2. If `s[i] > s[j]`, swap them.
3. Repeat until the whole string is sorted.

---

## 3. The "Aha!" Moment
Characters are integers (ASCII). Standard sorting algorithms like `std::sort()` work perfectly on strings.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <algorithm>

/**
 * Strategy: Standard Sort
 */
void sortString(std::string &s) {
    std::sort(s.begin(), s.end());
}

int main() {
    std::string s = "programming";
    sortString(s);
    std::cout << "Sorted: " << s << std::endl;
    return 0;
}
```
