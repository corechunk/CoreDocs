# 48 | Word Wrap Basics

Insert newlines into a string to prevent lines from exceeding a max width.

---

## 1. The Objective
Given `"The quick brown fox"`, `width=10`, return:
```text
The quick
brown fox
```

---

## 2. Visual Logic
### The "Line Buffer" Strategy
1. Keep track of current line length.
2. For each word:
   - If `currentLen + wordLen + 1 > maxWidth`:
     - Add `\n`, reset `currentLen = wordLen`.
   - Else:
     - Add space + word, update `currentLen`.

---

## 3. The "Aha!" Moment
You must decide whether to break mid-word or only at spaces. In this basic version, we assume words are smaller than the width and only break at spaces.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <sstream>
#include <vector>

/**
 * Strategy: Greedy word fitting
 */
std::string wrapText(std::string text, int width) {
    std::stringstream ss(text);
    std::string word, res = "", line = "";
    
    while (ss >> word) {
        if (line.length() + word.length() + 1 <= width) {
            if (!line.empty()) line += " ";
            line += word;
        } else {
            res += line + "\n";
            line = word;
        }
    }
    res += line;
    return res;
}

int main() {
    std::string s = "C++ problem solving is about logic and efficiency";
    std::cout << wrapText(s, 15) << std::endl;
    return 0;
}
```
