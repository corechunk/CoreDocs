# 14 | Remove Duplicate Characters

Keep only the first occurrence of each character.

---

## 1. The Objective
Given `"programming"`, return `"progamin"`.

---

## 2. Visual Logic
### The "Already Seen" Filter
1. Create a boolean array `seen[256]` set to false.
2. For each character `c`:
   - If `seen[c]` is false: Add to result, set `seen[c]` to true.
   - If `seen[c]` is true: Ignore.

---

## 3. The "Aha!" Moment
A frequency map (or boolean set) is the fastest way to perform a "Have I been here before?" check in $O(1)$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: Boolean Masking
 * Efficiency: Time O(n), Space O(1)
 */
std::string removeDuplicates(std::string s) {
    bool seen[256] = {false};
    std::string result = "";
    
    for (char c : s) {
        if (!seen[(unsigned char)c]) {
            result += c;
            seen[(unsigned char)c] = true;
        }
    }
    return result;
}

int main() {
    std::cout << "Original: mississippi" << std::endl;
    std::cout << "Unique: " << removeDuplicates("mississippi") << std::endl;
    return 0;
}
```
