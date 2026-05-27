# 47 | Longest Palindrome that can be Built

Determine the maximum length of a palindrome using given characters.

---

## 1. The Objective
Given `"abccccdd"`, you can build `"dccaccd"` (length 7).

---

## 2. Visual Logic
### The "Pairs and Single" Strategy
To build a palindrome:
1. Every character with an **Even** count can be fully used (half on left, half on right).
2. For characters with an **Odd** count, use `count - 1` (to make it even).
3. At the very end, you can add exactly **one** single character in the center.

---

## 3. The "Aha!" Moment
You don't need to arrange the string! Just count frequencies and sum up the even parts.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <unordered_map>

int longestPalindrome(std::string s) {
    std::unordered_map<char, int> freq;
    for (char c : s) freq[c]++;
    
    int length = 0;
    bool hasOdd = false;
    
    for (auto const& [c, count] : freq) {
        length += (count / 2) * 2;
        if (count % 2 == 1) hasOdd = true;
    }
    
    return hasOdd ? length + 1 : length;
}

int main() {
    std::cout << "Max Palindrome Length: " << longestPalindrome("abccccdd") << std::endl;
    return 0;
}
```
