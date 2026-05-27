# 46 | Longest Common Prefix

Find the longest string that is a prefix of all strings in a set.

---

## 1. The Objective
Given `["flower", "flow", "flight"]`, return `"fl"`.

---

## 2. Visual Logic
### The "Horizontal Scan" Strategy
1. Assume the first word is the prefix.
2. Compare it with the second word. Trim the prefix until it matches.
3. Compare the trimmed prefix with the third word. Trim again.
4. Continue until all words are checked or prefix is empty.

---

## 3. The "Aha!" Moment
A common prefix cannot be longer than the shortest word. Each comparison can only make the prefix **shorter**, never longer.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <string>

/**
 * Strategy: Iterative Trimming
 */
std::string longestCommonPrefix(std::vector<std::string>& strs) {
    if (strs.empty()) return "";
    
    std::string prefix = strs[0];
    for (int i = 1; i < strs.size(); i++) {
        while (strs[i].find(prefix) != 0) {
            prefix = prefix.substr(0, prefix.length() - 1);
            if (prefix.empty()) return "";
        }
    }
    return prefix;
}

int main() {
    std::vector<std::string> v = {"cluster", "clutch", "club"};
    std::cout << "LCP: " << longestCommonPrefix(v) << std::endl;
    return 0;
}
```
