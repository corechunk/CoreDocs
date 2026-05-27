# 28 | Group by Frequency

Group all elements that appear the same number of times.

---

## 1. The Objective
Given `[1, 1, 2, 3, 3, 4]`, return:
`Freq 1: [2, 4], Freq 2: [1, 3]`.

---

## 2. Visual Logic
### The "Inverse Map"
1. Frequency Map: `val -> freq`.
2. Inverse Map: `freq -> list of vals`.

---

## 3. The "Aha!" Moment
This is essentially "Bucket Sort Logic" (Problem 22) used for classification instead of selection.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

void groupByFreq(const std::vector<int>& arr) {
    std::unordered_map<int, int> freq;
    for (int x : arr) freq[x]++;
    
    std::unordered_map<int, std::vector<int>> inverse;
    for (auto const& [val, f] : freq) {
        inverse[f].push_back(val);
    }
    
    for (auto const& [f, vals] : inverse) {
        std::cout << "Freq " << f << ": ";
        for (int v : vals) std::cout << v << " ";
        std::cout << std::endl;
    }
}

int main() {
    std::vector<int> v = {1, 2, 2, 3, 3, 3, 4, 5, 5};
    groupByFreq(v);
    return 0;
}
```
