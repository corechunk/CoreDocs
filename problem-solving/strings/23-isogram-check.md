# 23 | Isogram Check

Check if a string has no repeating characters.

---

## 1. The Objective
An **Isogram** is a word where every letter appears exactly once.
- **Example:** `"machine"`. (True)
- **Example:** `"hello"`. (False)

---

## 2. Visual Logic
### The "Early Exit" Strategy
1. Keep a set of seen characters.
2. If you ever encounter a character that is **already** in the set, stop immediately.

---

## 3. The "Aha!" Moment
This is similar to "Remove Duplicates," but instead of removing them, we use the duplication as a "failure signal."

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <unordered_set>

/**
 * Strategy: Early detection via hashing
 */
bool isIsogram(std::string s) {
    std::unordered_set<char> seen;
    for (char c : s) {
        char lower = std::tolower(c);
        if (seen.count(lower)) return false;
        seen.insert(lower);
    }
    return true;
}

int main() {
    std::cout << "Is 'Alphabet' isogram? " << (isIsogram("Alphabet") ? "Yes" : "No") << std::endl;
    return 0;
}
```
