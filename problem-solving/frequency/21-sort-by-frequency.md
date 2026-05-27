# 21 | Sort by Frequency

Sort array elements based on how many times they appear.

---

## 1. The Objective
Given `[4, 4, 2, 2, 2, 5]`, return `[2, 2, 2, 4, 4, 5]`.

---

## 2. Visual Logic
### The "Weighting" Strategy
1. Count frequencies: `4:2, 2:3, 5:1`.
2. Define a custom comparison:
   - If `freq[A] > freq[B]`: A comes before B.
   - If `freq[A] == freq[B]`: Compare values (optional).

---

## 3. The "Aha!" Moment
Standard sorting uses the **Value**. Frequency sorting uses a **Mapped Value** as the priority.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>
#include <algorithm>

void sortByFreq(std::vector<int>& arr) {
    std::unordered_map<int, int> freq;
    for (int x : arr) freq[x]++;
    
    std::sort(arr.begin(), arr.end(), [&](int a, int b) {
        if (freq[a] != freq[b]) return freq[a] > freq[b];
        return a < b; // Secondary sort by value
    });
}

int main() {
    std::vector<int> v = {4, 4, 2, 2, 2, 5};
    sortByFreq(v);
    for (int x : v) std::cout << x << " ";
    return 0;
}
```
