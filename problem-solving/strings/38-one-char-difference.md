# 38 | One Edit Difference

Check if two strings differ by exactly one edit (insert, delete, or replace).

---

## 1. The Objective
- `"pale"`, `"ple"` -> `true` (Delete 'a')
- `"pales"`, `"pale"` -> `true` (Insert 's')
- `"pale"`, `"bale"` -> `true` (Replace 'p')
- `"pale"`, `"bake"` -> `false` (Two edits)

---

## 2. Visual Logic
### The "Pointer Alignment" Strategy
1. If lengths differ by $> 1$: `false`.
2. Compare chars index-by-index.
3. On first mismatch:
   - If lengths equal: Try replacing and continue.
   - If lengths differ: Skip one char in the longer string and continue.

---

## 3. The "Aha!" Moment
You only get **one** chance to skip or replace. If you find a second mismatch after your "edit credit" is used, the answer is `false`.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <cmath>

/**
 * Strategy: Edit Credit Tracking
 */
bool isOneEditAway(std::string s1, std::string s2) {
    if (std::abs((int)s1.length() - (int)s2.length()) > 1) return false;
    
    std::string shorter = s1.length() < s2.length() ? s1 : s2;
    std::string longer = s1.length() < s2.length() ? s2 : s1;
    
    int i = 0, j = 0;
    bool foundDiff = false;
    
    while (i < shorter.length() && j < longer.length()) {
        if (shorter[i] != longer[j]) {
            if (foundDiff) return false; // Already used the edit
            foundDiff = true;
            
            if (shorter.length() == longer.length()) i++; // Replace case
        } else {
            i++;
        }
        j++; // Always increment longer string pointer
    }
    return true;
}

int main() {
    std::cout << "pale vs ple: " << (isOneEditAway("pale", "ple") ? "True" : "False") << std::endl;
    std::cout << "pale vs bale: " << (isOneEditAway("pale", "bale") ? "True" : "False") << std::endl;
    return 0;
}
```
