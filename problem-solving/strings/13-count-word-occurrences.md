# 13 | Count Word Occurrences

Count how many times a specific word appears in a sentence.

---

## 1. The Objective
Given `"the cat and the dog"` and word `"the"`, return `2`.

---

## 2. Visual Logic
### The "Split and Compare" Strategy
1. Use a string stream or manual parser to extract "words" separated by spaces.
2. Compare each word with the target.

---

## 3. The "Aha!" Moment
Use `stringstream` in C++ to easily extract words without worrying about complex space/index math.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <sstream>

/**
 * Strategy: Tokenization (Word splitting)
 */
int countWords(std::string sentence, std::string target) {
    std::stringstream ss(sentence);
    std::string word;
    int count = 0;
    
    while (ss >> word) {
        if (word == target) {
            count++;
        }
    }
    return count;
}

int main() {
    std::string s = "blue sky blue sea blue ocean";
    std::cout << "Occurrences of 'blue': " << countWords(s, "blue") << std::endl;
    return 0;
}
```
