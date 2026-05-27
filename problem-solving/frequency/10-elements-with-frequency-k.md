# 10 | Elements with Frequency K

Find all elements that appear exactly $K$ times.

---

## 1. The Objective
Given `[1, 2, 2, 3, 3, 3]` and `K=2`, return `[2]`.

---

## 2. Visual Logic
1. Build frequency map: `1:1, 2:2, 3:3`.
2. Iterate through map entries.
3. If `entry.value == K`, add `entry.key` to result.

---

## 3. The "Aha!" Moment
This is the generalized version of "Find Unique" (K=1). Mapping allows you to answer any "Count" related query about your data.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

/**
 * Strategy: HashMap Filtering
 */
std::vector<int> elementsWithFreqK(const std::vector<int>& arr, int k) {
    std::unordered_map<int, int> freq;
    for (int x : arr) freq[x]++;
    
    std::vector<int> res;
    for (auto const& [val, count] : freq) {
        if (count == k) res.push_back(val);
    }
    return res;
}

int main() {
    std::vector<int> v = {1, 1, 2, 3, 3, 3, 4, 4};
    auto res = elementsWithFreqK(v, 2);
    for (int x : res) std::cout << x << " ";
    return 0;
}
```
