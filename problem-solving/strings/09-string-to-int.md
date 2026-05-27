# 09 | String to Integer (Manual)

Convert a numeric string to its integer value without `stoi()`.

---

## 1. The Objective
Given `"123"`, return the integer `123`.

---

## 2. Visual Logic
### The "Place Value" Build
1. Start with `result = 0`.
2. Get first digit: `'1' - '0' = 1`.
3. `result = 0 * 10 + 1 = 1`.
4. Get next: `'2' - '0' = 2`.
5. `result = 1 * 10 + 2 = 12`.
6. Get next: `'3' - '0' = 3`.
7. `result = 12 * 10 + 3 = 123`.

---

## 3. The "Aha!" Moment
To convert a character digit like `'5'` to the number `5`, subtract the ASCII value of `'0'`. Multiplying the previous result by 10 "shifts" it to the left to make room for the new digit.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Iterative Accumulation
 * Efficiency: Time O(n), Space O(1)
 */
int manualStoi(std::string s) {
    int res = 0;
    int sign = 1;
    int i = 0;
    
    // Handle negative sign
    if (s[0] == '-') {
        sign = -1;
        i = 1;
    }
    
    for (; i < s.length(); i++) {
        if (s[i] >= '0' && s[i] <= '9') {
            res = res * 10 + (s[i] - '0');
        }
    }
    return res * sign;
}

int main() {
    std::string s = "-456";
    std::cout << "String: " << s << " -> Int: " << manualStoi(s) << std::endl;
    return 0;
}
```
