# 23 | Sort String by Frequency

Rearrange a string so characters appearing most often come first.

---

## 1. The Objective
Given `"tree"`, return `"eert"` (or `"eetr"`).

---

## 2. Visual Logic
### The "Signature" Rebuild
1. Map: `t:1, r:1, e:2`.
2. Pairs: `(2, 'e'), (1, 't'), (1, 'r')`.
3. Sort pairs by frequency.
4. Construct: `'e'*2 + 't'*1 + 'r'*1`.

---

## 3. The "Aha!" Moment
Identical to Problem 21, but instead of sorting the input, you construct a **New String** based on the frequency priorities.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <string>
#include <vector>
#include <unordered_map>
#include <algorithm>

std::string frequencySort(std::string s) {
    std::unordered_map<char, int> freq;
    for (char c : s) freq[c]++;
    
    std::vector<std::pair<int, char>> v;
    for (auto const& [c, f] : freq) v.push_back({f, c});
    
    std::sort(v.rbegin(), v.rend()); // Sort descending
    
    std::string res = "";
    for (auto const& p : v) {
        res += std::string(p.first, p.second);
    }
    return res;
}

int main() {
    std::cout << "Sorted 'banana': " << frequencySort("banana") << std::endl;
    return 0;
}
```
