# 22 | Top K Frequent Elements

Find the $K$ most frequent elements in an array.

---

## 1. The Objective
Given `[1, 1, 1, 2, 2, 3]` and `K=2`, return `[1, 2]`.

---

## 2. Visual Logic
### The "Bucket Sort" Strategy
1. Build frequency map: `1:3, 2:2, 3:1`.
2. Create buckets where the **index** is the frequency.
   - Bucket 3: `[1]`
   - Bucket 2: `[2]`
   - Bucket 1: `[3]`
3. Collect from the highest bucket downwards until you have $K$ items.

---

## 3. The "Aha!" Moment
Bucket sort allows you to find Top-K in $O(n)$ time, avoiding the $O(n \log n)$ cost of a full sort.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

std::vector<int> topKFrequent(std::vector<int>& nums, int k) {
    std::unordered_map<int, int> counts;
    for (int n : nums) counts[n]++;
    
    int maxFreq = nums.size();
    std::vector<std::vector<int>> buckets(maxFreq + 1);
    for (auto const& [val, freq] : counts) {
        buckets[freq].push_back(val);
    }
    
    std::vector<int> res;
    for (int i = maxFreq; i >= 0 && res.size() < k; i--) {
        for (int val : buckets[i]) {
            res.push_back(val);
            if (res.size() == k) break;
        }
    }
    return res;
}

int main() {
    std::vector<int> v = {1, 1, 1, 2, 2, 3};
    auto res = topKFrequent(v, 2);
    for (int x : res) std::cout << x << " ";
    return 0;
}
```
