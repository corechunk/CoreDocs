# 20 | String Rotation

Shift all characters in a string by $k$ positions.

---

## 1. The Objective
Given `"hello"` and `k=2` (Left), return `"llohe"`.

---

## 2. Visual Logic
### The "Slice and Flip" Strategy
1. Take the first $k$ characters: `"he"`.
2. Take the rest: `"llo"`.
3. Combine: `"llo" + "he"`.

---

## 3. The "Aha!" Moment
Instead of moving characters one by one, use the `substr()` function to perform "bulk moves."

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Substring Concatenation
 */
std::string rotateLeft(std::string s, int k) {
    int n = s.length();
    k %= n; // Handle k > n
    return s.substr(k) + s.substr(0, k);
}

std::string rotateRight(std::string s, int k) {
    int n = s.length();
    k %= n;
    return s.substr(n - k) + s.substr(0, n - k);
}

int main() {
    std::string s = "abcdef";
    std::cout << "Left 2: " << rotateLeft(s, 2) << std::endl;
    std::cout << "Right 2: " << rotateRight(s, 2) << std::endl;
    return 0;
}
```
