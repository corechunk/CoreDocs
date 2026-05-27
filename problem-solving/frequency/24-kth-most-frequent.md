# 24 | Kth Most Frequent Element

Find the element that ranks $K^{th}$ in frequency.

---

## 1. The Objective
Given `[1, 1, 2, 2, 2, 3, 3, 3, 3]` and `K=2`, return `2`.
(Rank 1: '3' with freq 4, Rank 2: '2' with freq 3).

---

## 2. Visual Logic
1. Build frequency map.
2. Store unique frequencies in a sorted list.
3. Find the $K^{th}$ value in that list.

---

## 3. The "Aha!" Moment
You don't need to sort the whole array. You only need to sort the **Counts**.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>
#include <algorithm>

int kthFrequent(const std::vector<int>& arr, int k) {
    std::unordered_map<int, int> freq;
    for (int x : arr) freq[x]++;
    
    std::vector<std::pair<int, int>> counts;
    for (auto const& [val, f] : freq) counts.push_back({f, val});
    
    std::sort(counts.rbegin(), counts.rend());
    
    if (k <= counts.size()) return counts[k-1].second;
    return -1;
}

int main() {
    std::vector<int> v = {1,1,2,2,2,3,3,3,3};
    std::cout << "2nd most frequent: " << kthFrequent(v, 2) << std::endl;
    return 0;
}
```
