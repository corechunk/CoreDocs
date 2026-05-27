# 25 | Relative Sort Order

Sort array `A1` according to the order of elements in `A2`.

---

## 1. The Objective
Given `A1 = [2, 3, 1, 3, 2, 4, 6, 7, 9]` and `A2 = [2, 1, 4, 3]`, return:
`[2, 2, 1, 4, 3, 3, 6, 7, 9]`.
(Elements in A2 come first in their specific order, others follow).

---

## 2. Visual Logic
### The "Priority Consumer"
1. Build frequency map of A1.
2. For every element `x` in A2:
   - Append `x` to result `freq[x]` times.
   - Delete `x` from map.
3. Sort remaining map keys and append to result.

---

## 3. The "Aha!" Moment
Mapping allows you to "extract" specific priorities from a dataset while keeping the leftovers for later processing.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <map> // Using ordered map for automatic sorting of leftovers

std::vector<int> relativeSort(std::vector<int>& a1, std::vector<int>& a2) {
    std::map<int, int> freq;
    for (int x : a1) freq[x]++;
    
    std::vector<int> res;
    for (int x : a2) {
        while (freq[x] > 0) {
            res.push_back(x);
            freq[x]--;
        }
        freq.erase(x);
    }
    
    for (auto const& [val, count] : freq) {
        for (int i = 0; i < count; i++) res.push_back(val);
    }
    return res;
}

int main() {
    std::vector<int> a1 = {2,1,2,5,7,1,9,3}, a2 = {2,1,3};
    auto res = relativeSort(a1, a2);
    for (int x : res) std::cout << x << " ";
    return 0;
}
```
