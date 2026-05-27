# 38 | Find All Anagrams in String

Return starting indices of all anagrams of `P` within `S`.

---

## 1. The Objective
`S = "cbaebabacd"`, `P = "abc"`. 
Anagrams start at 0 (`cba`) and 6 (`bac`).

---

## 2. Visual Logic
### The "Sliding Frequency" Strategy
1. Build frequency map for P.
2. Use a sliding window of size `P.length()`.
3. If window map matches P map, found an index!

---

## 3. The "Aha!" Moment
Use an array `int freq[26]` to represent maps. Comparing two 26-size arrays is $O(1)$, making the total time $O(n)$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <string>

std::vector<int> findAnagrams(std::string s, std::string p) {
    if (s.length() < p.length()) return {};
    std::vector<int> target(26, 0), window(26, 0), res;
    
    for (char c : p) target[c - 'a']++;
    
    for (int i = 0; i < s.length(); i++) {
        window[s[i] - 'a']++;
        if (i >= p.length()) {
            window[s[i - p.length()] - 'a']--;
        }
        if (window == target) res.push_back(i - p.length() + 1);
    }
    return res;
}

int main() {
    auto res = findAnagrams("abab", "ab");
    for (int x : res) std::cout << x << " ";
    return 0;
}
```
