# 30 | Distinct Elements in Window

Count unique elements in every sliding window of size $K$.

---

## 1. The Objective
Given `[1, 2, 1, 3, 4, 2, 3]` and `K=4`, return:
Window 1 `[1,2,1,3]` -> **3** unique.
Window 2 `[2,1,3,4]` -> **4** unique.
...

---

## 2. Visual Logic
### The "Add-Delete" Strategy
1. Build map for first window.
2. For each slide:
   - Increment count for **new** element.
   - Decrement count for **old** element.
   - If count hits 0, remove from map.
   - Result is `map.size()`.

---

## 3. The "Aha!" Moment
Don't clear the map every time! Sliding the window means only two elements change. The rest of your frequency map stays valid.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

void countDistinct(const std::vector<int>& arr, int k) {
    std::unordered_map<int, int> freq;
    
    // Initial window
    for (int i = 0; i < k; i++) freq[arr[i]]++;
    std::cout << freq.size() << " ";
    
    // Slide
    for (int i = k; i < arr.size(); i++) {
        // Remove outgoing
        int out = arr[i - k];
        if (freq[out] == 1) freq.erase(out);
        else freq[out]--;
        
        // Add incoming
        freq[arr[i]]++;
        
        std::cout << freq.size() << " ";
    }
}

int main() {
    std::vector<int> v = {1, 2, 1, 3, 4, 2, 3};
    countDistinct(v, 4);
    return 0;
}
```
