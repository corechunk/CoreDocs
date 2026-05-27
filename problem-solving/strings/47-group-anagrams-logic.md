# 47 | Group Anagrams Logic

Identify sets of words that are anagrams of each other.

---

## 1. The Objective
Given `["eat", "tea", "tan", "ate", "nat", "bat"]`, group them.
Result: `[[eat, tea, ate], [tan, nat], [bat]]`.

---

## 2. Visual Logic
### The "Sorted Key" Strategy
1. For every word, create a "signature" by sorting its letters.
   - `eat` -> `aet`
   - `tea` -> `aet`
   - `tan` -> `ant`
2. Words with the same signature belong together.

---

## 3. The "Aha!" Moment
Using a `map<string, vector<string>>` allows you to collect all words under their sorted signature in a single pass.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <string>
#include <algorithm>
#include <map>

/**
 * Strategy: Sorting as Hashing
 */
void groupAnagrams(std::vector<std::string>& strs) {
    std::map<std::string, std::vector<std::string>> groups;
    
    for (std::string s : strs) {
        std::string key = s;
        std::sort(key.begin(), key.end());
        groups[key].push_back(s);
    }
    
    for (auto const& [key, val] : groups) {
        std::cout << "[ ";
        for (std::string s : val) std::cout << s << " ";
        std::cout << "]" << std::endl;
    }
}

int main() {
    std::vector<std::string> v = {"listen", "silent", "apple", "pale", "plea"};
    groupAnagrams(v);
    return 0;
}
```
