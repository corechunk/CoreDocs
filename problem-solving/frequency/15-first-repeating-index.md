# 15 | First Repeating Element Index

Find the element that repeats earliest in the array.

---

## 1. The Objective
Given `[6, 10, 5, 4, 9, 120, 4, 6, 10]`, return `6` (at index 0).
**Note:** Even though 4 repeats, 6's **first** occurrence is earlier.

---

## 2. Visual Logic
### The "Reverse Tracker"
1. Iterate from **Right to Left**.
2. Keep a Set of seen items.
3. If current item is in Set, update `minIndex = current_index`.

---

## 3. The "Aha!" Moment
By scanning backwards, the last "duplicate" you encounter from the back is actually the **first** one from the front.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>

int firstRepeating(const std::vector<int>& arr) {
    int minIdx = -1;
    std::unordered_set<int> seen;
    
    for (int i = arr.size() - 1; i >= 0; i--) {
        if (seen.count(arr[i])) {
            minIdx = i;
        } else {
            seen.insert(arr[i]);
        }
    }
    return (minIdx != -1) ? arr[minIdx] : -1;
}

int main() {
    std::vector<int> v = {10, 5, 3, 4, 3, 5, 6};
    std::cout << "First repeating: " << firstRepeating(v) << std::endl;
    return 0;
}
```
