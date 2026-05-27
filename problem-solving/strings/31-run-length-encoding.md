# 31 | Run-Length Encoding

Compress a string by counting repeated characters.

---

## 1. The Objective
Given `"aaabbcccc"`, return `"a3b2c4"`.

---

## 2. Visual Logic
### The "Run Counter" Strategy
1. Start at first char. Count consecutive matches.
2. When the character changes:
   - Append `char` and `count` to result.
   - Reset count to 1 for the new char.

```text
a a a b b c c c c
|---3| |---2| |---4|
```

---

## 3. The "Aha!" Moment
Iterate from `0` to `length - 1`. Always check if `s[i] == s[i+1]`. Be careful not to go out of bounds on the last character!

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Consecutive Match Counting
 */
std::string encodeRLE(std::string s) {
    std::string res = "";
    int n = s.length();
    
    for (int i = 0; i < n; i++) {
        int count = 1;
        while (i < n - 1 && s[i] == s[i + 1]) {
            count++;
            i++;
        }
        res += s[i] + std::to_string(count);
    }
    return res;
}

int main() {
    std::string s = "wwwwaaadexxxxxx";
    std::cout << "Encoded: " << encodeRLE(s) << std::endl;
    return 0;
}
```
