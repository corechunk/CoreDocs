# 43 | Random Pick with Weight

Pick an item randomly where frequency determines the probability.

---

## 1. The Objective
Given `A: 10, B: 2, C: 1`, item A should be picked 10/13 of the time.

---

## 2. Visual Logic
### The "Prefix Range" Strategy
1. Construct a cumulative weight array: `[10, 12, 13]`.
2. Generate a random number `r` from 1 to 13.
3. Find where `r` fits:
   - $1 \le r \le 10 \to$ Pick A.
   - $11 \le r \le 12 \to$ Pick B.
   - $r = 13 \to$ Pick C.

---

## 3. The "Aha!" Moment
By turning frequencies into a "Line of segments," you map a uniform random number into a weighted probability space.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <numeric>
#include <cstdlib>
#include <ctime>

char pickWeighted(const std::vector<std::pair<char, int>>& weights) {
    std::vector<int> prefixSums;
    int total = 0;
    for (auto const& p : weights) {
        total += p.second;
        prefixSums.push_back(total);
    }
    
    int r = (rand() % total) + 1;
    for (int i = 0; i < prefixSums.size(); i++) {
        if (r <= prefixSums[i]) return weights[i].first;
    }
    return '?';
}

int main() {
    srand(time(0));
    std::vector<std::pair<char, int>> w = {{'A', 10}, {'B', 2}, {'C', 1}};
    std::cout << "Picked: " << pickWeighted(w) << std::endl;
    return 0;
}
```
