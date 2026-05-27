# 35 | Reverse Words in Sentence

Flip the order of words without reversing the words themselves.

---

## 1. The Objective
Given `"Sky is blue"`, return `"blue is Sky"`.

---

## 2. Visual Logic
### The "Double Flip" Strategy
1. Reverse the entire string: `"eulb si ykS"`.
2. Now, reverse each word in-place: `"blue is Sky"`.

---

## 3. The "Aha!" Moment
By reversing twice, the characters end up in their original internal word order, but the word positions are swapped!

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <algorithm>

/**
 * Strategy: Global Reverse + Local Word Reverse
 */
void reverseWords(std::string &s) {
    // 1. Reverse entire sentence
    std::reverse(s.begin(), s.end());
    
    // 2. Reverse each word
    int start = 0;
    for (int i = 0; i <= s.length(); i++) {
        if (i == s.length() || s[i] == ' ') {
            std::reverse(s.begin() + start, s.begin() + i);
            start = i + 1;
        }
    }
}

int main() {
    std::string s = "The quick brown fox";
    reverseWords(s);
    std::cout << "Reversed Words: " << s << std::endl;
    return 0;
}
```
