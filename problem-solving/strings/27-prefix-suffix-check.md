# 27 | Prefix & Suffix Check

Check if a string starts or ends with a specific sequence.

---

## 1. The Objective
Given `"homework"`, check if it starts with `"home"` and ends with `"work"`.

---

## 2. Visual Logic
### The "Direct Comparison"
- **Prefix:** Compare `s[0...m-1]` with `prefix`.
- **Suffix:** Compare `s[n-m...n-1]` with `suffix`.

---

## 3. The "Aha!" Moment
Use `substr()` or a manual loop. For the suffix, the starting index in the main string is always `(main_length - suffix_length)`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Offset Matching
 */
bool startsWith(std::string s, std::string pre) {
    if (pre.length() > s.length()) return false;
    return s.substr(0, pre.length()) == pre;
}

bool endsWith(std::string s, std::string suf) {
    if (suf.length() > s.length()) return false;
    return s.substr(s.length() - suf.length()) == suf;
}

int main() {
    std::string s = "javascript";
    std::cout << "Starts with 'java'? " << startsWith(s, "java") << std::endl;
    std::cout << "Ends with 'script'? " << endsWith(s, "script") << std::endl;
    return 0;
}
```
