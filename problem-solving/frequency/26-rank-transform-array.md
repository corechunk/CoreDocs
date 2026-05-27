# 26 | Rank Transform of Array

Replace every element with its "rank" (the index it would have in a sorted unique list).

---

## 1. The Objective
Given `[40, 10, 20, 30]`, return `[4, 1, 2, 3]`.
Given `[10, 10, 10]`, return `[1, 1, 1]`.

---

## 2. Visual Logic
### The "Leaderboard" Mapping
1. Sort unique elements: `[10, 20, 30, 40]`.
2. Map value to rank: `10->1, 20->2, 30->3, 40->4`.
3. Iterate through original array and replace with mapped rank.

---

## 3. The "Aha!" Moment
A rank transform is just a **Value-to-Index** mapping. Using a sorted set ensures ranks are assigned correctly and duplicates share the same rank.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <set>
#include <unordered_map>

std::vector<int> rankTransform(const std::vector<int>& arr) {
    std::set<int> unique(arr.begin(), arr.end());
    std::unordered_map<int, int> valToRank;
    
    int rank = 1;
    for (int x : unique) {
        valToRank[x] = rank++;
    }
    
    std::vector<int> res;
    for (int x : arr) res.push_back(valToRank[x]);
    return res;
}

int main() {
    std::vector<int> v = {10, 30, 20, 10};
    auto res = rankTransform(v);
    for (int x : res) std::cout << x << " ";
    return 0;
}
```
