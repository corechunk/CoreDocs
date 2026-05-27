# 37 | Word Pattern Check

Check if a pattern (e.g., `abba`) matches a sequence of words.

---

## 1. The Objective
`pattern = "abba"`, `str = "dog cat cat dog"` -> `true`.
`pattern = "abba"`, `str = "dog cat cat fish"` -> `false`.

---

## 2. Visual Logic
### The "Parallel Map" Strategy
Map char `a` to word `"dog"`.
Map word `"dog"` back to char `a`.
Ensure no character or word breaks this one-to-one relationship.

---

## 3. The "Aha!" Moment
This is the Isomorphic logic applied between two different types (Char and String).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <vector>
#include <sstream>
#include <unordered_map>

bool wordPattern(std::string pattern, std::string s) {
    std::stringstream ss(s);
    std::string word;
    std::vector<std::string> words;
    while (ss >> word) words.push_back(word);
    
    if (pattern.length() != words.size()) return false;
    
    std::unordered_map<char, std::string> c2w;
    std::unordered_map<std::string, char> w2c;
    
    for (int i = 0; i < pattern.length(); i++) {
        char c = pattern[i];
        std::string w = words[i];
        
        if (c2w.count(c) && c2w[c] != w) return false;
        if (w2c.count(w) && w2c[w] != c) return false;
        
        c2w[c] = w;
        w2c[w] = c;
    }
    return true;
}

int main() {
    std::cout << "Match? " << wordPattern("abba", "dog cat cat dog") << std::endl;
    return 0;
}
```
