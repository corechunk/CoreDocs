# 35 | Smallest Window containing all Chars

Find the minimum substring that contains every character from a set.

---

## 1. The Objective
Given `S = "ADOBECODEBANC"` and `T = "ABC"`, return `"BANC"`.

---

## 2. Visual Logic
### The "Elastic Sliding Window"
1. Expand `right` until you have all chars from T.
2. Shrink `left` as long as you still have all chars.
3. Record minimum window.
4. Repeat.

---

## 3. The "Aha!" Moment
You need two maps: one for the "Requirement" and one for the "Current Window." This ensures you keep track of both character types AND their counts.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <unordered_map>
#include <climits>

std::string minWindow(std::string s, std::string t) {
    std::unordered_map<char, int> target;
    for (char c : t) target[c]++;
    
    std::unordered_map<char, int> window;
    int left = 0, right = 0, required = target.size(), formed = 0;
    int minLen = INT_MAX, bestL = 0;
    
    while (right < s.length()) {
        char c = s[right];
        window[c]++;
        if (target.count(c) && window[c] == target[c]) formed++;
        
        while (formed == required) {
            if (right - left + 1 < minLen) {
                minLen = right - left + 1;
                bestL = left;
            }
            char leftC = s[left];
            window[leftC]--;
            if (target.count(leftC) && window[leftC] < target[leftC]) formed--;
            left++;
        }
        right++;
    }
    return (minLen == INT_MAX) ? "" : s.substr(bestL, minLen);
}

int main() {
    std::cout << "Smallest window: " << minWindow("ADOBECODEBANC", "ABC") << std::endl;
    return 0;
}
```
