# 30 | Longest Word in Sentence

Find the word with the maximum character count.

---

## 1. The Objective
Given `"The quick brown fox jumps"`, return `"quick"` (or `"brown"`).

---

## 2. Visual Logic
### The "King of the Hill" Strategy
1. Split sentence into words.
2. Initialize `maxWord = ""`.
3. For each word:
   - If `word.length > maxWord.length`:
     - `maxWord = word`.

---

## 3. The "Aha!" Moment
Use `stringstream` to iterate word-by-word. This avoids manual space-index tracking.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <sstream>

/**
 * Strategy: Tokenize and Compare
 */
std::string findLongestWord(std::string s) {
    std::stringstream ss(s);
    std::string word, longest = "";
    
    while (ss >> word) {
        if (word.length() > longest.length()) {
            longest = word;
        }
    }
    return longest;
}

int main() {
    std::string s = "Computer Science is the study of computation";
    std::cout << "Longest: " << findLongestWord(s) << std::endl;
    return 0;
}
```
