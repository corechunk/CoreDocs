# 20 | Elements Appearing > N/K Times

Identify elements with a frequency higher than a specific ratio.

---

## 1. The Objective
Given an array of size $N$ and $K$, find elements with frequency $> N/K$.
- **Example:** `[3, 1, 2, 2, 1, 2, 3, 3]`, $K=4$. $N/K = 2$.
- Result: `[2, 3]` (both appear 3 times).

---

## 2. Visual Logic
1. Calculate the threshold $T = N/K$.
2. Build frequency map.
3. Filter entries where `value > T`.

---

## 3. The "Aha!" Moment
This is a standard statistical filter. The most famous version is **Majority Element** ($K=2$, frequency $> N/2$).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

void findFrequent(const std::vector<int>& arr, int k) {
    int n = arr.size();
    int threshold = n / k;
    std::unordered_map<int, int> freq;
    
    for (int x : arr) freq[x]++;
    
    for (auto const& [val, count] : freq) {
        if (count > threshold) {
            std::cout << val << " ";
        }
    }
}

int main() {
    std::vector<int> v = {3, 1, 2, 2, 1, 2, 3, 3};
    findFrequent(v, 4);
    return 0;
}
```
