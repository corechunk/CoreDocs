# 39 | String Compression Comparison

Compress a string only if it results in a shorter string.

---

## 1. The Objective
Given `"aabcccccaaa"`, return `"a2b1c5a3"`.
Given `"abc"`, return `"abc"` (since `"a1b1c1"` is longer).

---

## 2. Visual Logic
### The "Compressed Length" Check
1. Build the RLE compressed string (Problem 31).
2. Compare `result.length()` with `original.length()`.
3. Return the shorter one.

---

## 3. The "Aha!" Moment
Many compression algorithms have "overhead." For small or unique strings, raw data is more efficient than compressed data.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Conditional RLE
 */
std::string smartCompress(std::string s) {
    std::string compressed = "";
    int n = s.length();
    
    for (int i = 0; i < n; i++) {
        int count = 1;
        while (i < n - 1 && s[i] == s[i+1]) {
            count++;
            i++;
        }
        compressed += s[i] + std::to_string(count);
    }
    
    return (compressed.length() < s.length()) ? compressed : s;
}

int main() {
    std::cout << "Result: " << smartCompress("aabcccccaaa") << std::endl;
    std::cout << "Result: " << smartCompress("abc") << std::endl;
    return 0;
}
```
