# 10 | Integer to String (Manual)

Convert an integer to a string without `to_string()`.

---

## 1. The Objective
Given `789`, return the string `"789"`.

---

## 2. Visual Logic
### The "Extract and Reverse" Method
1. `789 % 10 = 9` (Char: '9')
2. `789 / 10 = 78`
3. `78 % 10 = 8` (Char: '8')
4. `78 / 10 = 7`
5. `7 % 10 = 7` (Char: '7')
**Extracted:** `9, 8, 7` $\to$ **Reverse** $\to$ `"789"`.

---

## 3. The "Aha!" Moment
Digits are extracted from right to left (last to first). Since strings are built from left to right, you must reverse the result at the end.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <algorithm>

/**
 * Strategy: Remainder Extraction + Reverse
 */
std::string manualToString(int n) {
    if (n == 0) return "0";
    
    std::string s = "";
    bool isNegative = false;
    if (n < 0) { isNegative = true; n = -n; }
    
    while (n > 0) {
        s += (char)((n % 10) + '0');
        n /= 10;
    }
    
    if (isNegative) s += '-';
    
    std::reverse(s.begin(), s.end());
    return s;
}

int main() {
    int num = -123;
    std::cout << "Num: " << num << " -> String: " << manualToString(num) << std::endl;
    return 0;
}
```
