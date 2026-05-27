# 42 | Longest Unique Substring

Find the length of the longest substring without repeating characters.

---

## 1. The Objective
Given `"abcabcbb"`, the longest unique substring is `"abc"`, length **3**.

---

## 2. Visual Logic
### The "Sliding Window" Strategy
1. Start window with `left = 0, right = 0`.
2. Move `right` and add characters to a set.
3. If you hit a duplicate:
   - Shrink the window from the `left` until the duplicate is gone.
4. Record the max `right - left + 1`.

---

## 3. The "Aha!" Moment
This is the **Dynamic Sliding Window**. It allows you to solve the problem in a single $O(n)$ pass instead of $O(n^2)$ by checking every possible starting point.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <vector>
#include <algorithm>

/**
 * Strategy: Sliding Window with Hash Array
 * Efficiency: Time O(n)
 */
int longestUnique(std::string s) {
    std::vector<int> lastIdx(256, -1);
    int maxLen = 0, start = 0;
    
    for (int i = 0; i < s.length(); i++) {
        char c = s[i];
        // If char seen before and is inside current window
        if (lastIdx[c] >= start) {
            start = lastIdx[c] + 1;
        }
        lastIdx[c] = i;
        maxLen = std::max(maxLen, i - start + 1);
    }
    return maxLen;
}

int main() {
    std::string s = "abcabcbb";
    std::cout << "Longest unique length: " << longestUnique(s) << std::endl;
    return 0;
}
```
