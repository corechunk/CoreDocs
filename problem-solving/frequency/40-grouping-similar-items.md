# 40 | Grouping Similar Items

Group items that share the same characteristics.

---

## 1. The Objective
Given a list of words, group them by their length.

---

## 2. Visual Logic
### The "Collector" Strategy
Map `Attribute -> List of items`.
```text
3 -> [cat, dog, bat]
4 -> [blue, frog]
```

---

## 3. The "Aha!" Moment
This is the generalized version of "Group Anagrams." Mapping allows you to partition any dataset based on a shared property.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>
#include <string>

void groupByLength(const std::vector<std::string>& strs) {
    std::unordered_map<int, std::vector<std::string>> groups;
    for (const std::string& s : strs) {
        groups[s.length()].push_back(s);
    }
    
    for (auto const& [len, list] : groups) {
        std::cout << "Length " << len << ": ";
        for (const std::string& s : list) std::cout << s << " ";
        std::cout << std::endl;
    }
}

int main() {
    std::vector<std::string> words = {"a", "the", "be", "to", "and"};
    groupByLength(words);
    return 0;
}
```
