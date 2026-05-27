# 12 | All Indices of a Character

Find every position where a specific character appears.

---

## 1. The Objective
Given `"hello world"` and `'o'`, return `[4, 7]`.

---

## 2. Visual Logic
### The "Scanner" Strategy
```text
Index: 0 1 2 3 4 5 6 7 8 9
String: h e l l o   w o r l d
Target:         ^       ^
```
Just iterate through the string and push the index $i$ into a list whenever `s[i] == target`.

---

## 3. The "Aha!" Moment
Simple linear search. Useful for finding all occurrences before performing a bulk replacement or analysis.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <vector>

/**
 * Strategy: Linear Index Collection
 */
std::vector<int> findIndices(std::string s, char target) {
    std::vector<int> positions;
    for (int i = 0; i < s.length(); i++) {
        if (s[i] == target) {
            positions.push_back(i);
        }
    }
    return positions;
}

int main() {
    std::string text = "banana";
    std::vector<int> res = findIndices(text, 'a');
    
    std::cout << "Found 'a' at: ";
    for (int idx : res) std::cout << idx << " ";
    std::cout << std::endl;
    return 0;
}
```
