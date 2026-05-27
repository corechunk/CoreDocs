# 03 | String Palindrome

Check if a string reads the same forwards and backwards.

---

## 1. The Objective
Given `"radar"`, return `true`. Given `"hello"`, return `false`.

---

## 2. Visual Logic
### The "Symmetry" Check
1. Start at both ends (Two-pointer).
2. Compare characters.
3. If any pair doesn't match, it's not a palindrome.

```text
r a d a r
^       ^  (match)
  ^   ^    (match)
    ^      (center, stop)
```

---

## 3. The "Aha!" Moment
Instead of reversing the whole string and comparing (which uses $O(n)$ extra space), you can verify symmetry in-place. This is faster and more memory-efficient.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Two-Pointer Comparison
 * Efficiency: Time O(n), Space O(1)
 */
bool isPalindrome(std::string s) {
    int left = 0;
    int right = s.length() - 1;
    
    while (left < right) {
        if (s[left] != s[right]) {
            return false;
        }
        left++;
        right--;
    }
    return true;
}

int main() {
    std::string test = "level";
    if (isPalindrome(test)) {
        std::cout << test << " is a palindrome." << std::endl;
    }
    return 0;
}
```
