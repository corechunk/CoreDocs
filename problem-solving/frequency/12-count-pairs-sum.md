# 12 | Count Pairs with Given Sum

Find the total number of pairs that sum to $K$.

---

## 1. The Objective
Given `[1, 5, 7, 1]` and `K = 6`, return `2`. (Pairs: `(1,5)` and `(5,1)`).

---

## 2. Visual Logic
### The "Frequency Multiplication"
If you find `x`, and you need `complement`.
The number of pairs you can form is exactly `freq[complement]`.

---

## 3. The "Aha!" Moment
Use a frequency map to keep track of how many times you’ve seen each number. For each new number, add the frequency of its complement to the total count.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

/**
 * Strategy: Cumulative frequency sum
 */
int countPairs(const std::vector<int>& arr, int k) {
    std::unordered_map<int, int> freq;
    int count = 0;
    
    for (int x : arr) {
        if (freq.count(k - x)) {
            count += freq[k - x];
        }
        freq[x]++;
    }
    return count;
}

int main() {
    std::vector<int> v = {1, 5, 7, 1, 5};
    std::cout << "Pairs with sum 6: " << countPairs(v, 6) << std::endl;
    return 0;
}
```
