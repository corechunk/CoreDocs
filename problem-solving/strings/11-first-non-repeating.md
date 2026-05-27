# 11 | First Non-Repeating Character

Find the first character that only appears once in the string.

---

## 1. The Objective
Given `"leetcode"`, return `'l'`. Given `"loveleetcode"`, return `'v'`.

---

## 2. Visual Logic
### The "Two-Pass" Frequency Map
1. **Pass 1:** Count how many times each character appears.
   ```text
   l:1, o:2, v:1, e:4 ...
   ```
2. **Pass 2:** Iterate through the string again. The first character whose count is 1 is the winner.

---

## 3. The "Aha!" Moment
Use an array of size 256 (ASCII range) or 26 (if lowercase only) to store counts. This reduces the problem from $O(n^2)$ to $O(n)$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <vector>

/**
 * Strategy: Frequency Array
 * Efficiency: Time O(n), Space O(1)
 */
char firstUnique(std::string s) {
    int count[256] = {0};
    
    // Pass 1: Build Frequency Map
    for (char c : s) count[(unsigned char)c]++;
    
    // Pass 2: Search for first count == 1
    for (char c : s) {
        if (count[(unsigned char)c] == 1) {
            return c;
        }
    }
    return '\0'; // None found
}

int main() {
    std::string text = "swiss";
    char result = firstUnique(text);
    if (result) std::cout << "First unique: " << result << std::endl;
    return 0;
}
```
