# 36 | Isomorphic Strings (Mapping Version)

Check if strings share structure using generic maps.

---

## 1. The Objective
Solve the Isomorphic check (Problem 44 String tier) using HashMaps.

---

## 2. Visual Logic
Map every character to the **Index of its first appearance**.
- `"egg"` -> `[0, 1, 1]`
- `"add"` -> `[0, 1, 1]`
- `[0, 1, 1] == [0, 1, 1]`? YES.

---

## 3. The "Aha!" Moment
Instead of a complex two-way mapping, transform both strings into a "Structural Sequence." If the structures match, the strings are isomorphic.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <unordered_map>
#include <vector>

std::vector<int> getStructure(std::string s) {
    std::unordered_map<char, int> m;
    std::vector<int> res;
    int id = 0;
    for (char c : s) {
        if (!m.count(c)) m[c] = id++;
        res.push_back(m[c]);
    }
    return res;
}

bool isIsomorphic(std::string s, std::string t) {
    return getStructure(s) == getStructure(t);
}

int main() {
    std::cout << "paper/title: " << isIsomorphic("paper", "title") << std::endl;
    return 0;
}
```
