# 17 | Replace Character

Replace all instances of character `A` with character `B`.

---

## 1. The Objective
Given `"apple"`, replace `'p'` with `'b'` to get `"abble"`.

---

## 2. Visual Logic
### The "Overwrite" Strategy
1. Iterate through the string.
2. If `s[i] == oldChar`:
   - Set `s[i] = newChar`.

---

## 3. The "Aha!" Moment
Strings in C++ are mutable (changeable). You don't need a new string; just modify the original indices directly.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>

/**
 * Strategy: In-place Overwrite
 */
void replaceChar(std::string &s, char oldC, char newC) {
    for (int i = 0; i < s.length(); i++) {
        if (s[i] == oldC) {
            s[i] = newC;
        }
    }
}

int main() {
    std::string s = "mississippi";
    replaceChar(s, 's', 'z');
    std::cout << "Replaced: " << s << std::endl;
    return 0;
}
```
