# 02 | Find Duplicates (Frequency Array)

Identify all elements that appear more than once.

---

## 1. The Objective
Given `[4, 3, 2, 7, 8, 2, 3, 1]`, return `[2, 3]`.

---

## 2. Visual Logic
### The "Flag" Strategy
1. Build frequency map.
2. Filter the map: Keep only items where `count > 1`.

---

## 3. The "Aha!" Moment
If you know the range of numbers (e.g., 1 to 100), you can use a fixed-size array `int count[101]` instead of a HashMap for maximum speed.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

/**
 * Strategy: Multi-pass filtering
 */
std::vector<int> findDuplicates(const std::vector<int>& arr) {
    std::unordered_map<int, int> freq;
    std::vector<int> dups;
    
    for (int x : arr) freq[x]++;
    
    for (auto const& [val, count] : freq) {
        if (count > 1) dups.push_back(val);
    }
    return dups;
}

int main() {
    std::vector<int> v = {1, 2, 3, 1, 2, 4};
    auto res = findDuplicates(v);
    for (int d : res) std::cout << d << " ";
    return 0;
}
```
