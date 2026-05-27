# 44 | Isomorphic Strings

Determine if two strings share the same mapping structure.

---

## 1. The Objective
Two strings are **Isomorphic** if characters in `A` can be replaced to get `B`.
- `"egg"`, `"add"` -> `true` (`e->a, g->d`)
- `"foo"`, `"bar"` -> `false` (`o` cannot map to both `a` and `r`)

---

## 2. Visual Logic
### The "One-to-One" Mapping
1. Map `e` to `a`.
2. Map `g` to `d`.
3. Check next `g`: It’s already mapped to `d`. Does B have `d`? YES.
Result: **TRUE**.

---

## 3. The "Aha!" Moment
You must maintain **two** maps: one from A to B and one from B to A. This ensures that two different characters in A don't map to the same character in B.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <vector>

/**
 * Strategy: Dual ASCII Mapping
 */
bool isIsomorphic(std::string s, std::string t) {
    if (s.length() != t.length()) return false;
    
    int mapS[256] = {0}, mapT[256] = {0};
    
    for (int i = 0; i < s.length(); i++) {
        char charS = s[i], charT = t[i];
        
        if (mapS[charS] == 0 && mapT[charT] == 0) {
            mapS[charS] = charT;
            mapT[charT] = charS;
        } else if (mapS[charS] != charT || mapT[charT] != charS) {
            return false;
        }
    }
    return true;
}

int main() {
    std::cout << "paper & title: " << (isIsomorphic("paper", "title") ? "Yes" : "No") << std::endl;
    return 0;
}
```
