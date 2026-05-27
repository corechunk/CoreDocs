# 16 | Last Repeating Element Index

Find the element whose duplicate appears latest in the array.

---

## 1. The Objective
Given `[1, 5, 3, 4, 3, 5, 6]`, return `5` (its second appearance is the last repeating event).

---

## 2. Visual Logic
### The "Occurrence Map"
1. Scan from left to right.
2. If item is NOT in the map, store its index.
3. If item IS in the map, update its `lastSeen` index and global `maxLastIndex`.

---

## 3. The "Aha!" Moment
This identifies the repeating element that "closes" the sequence of repetitions the latest.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

int lastRepeating(const std::vector<int>& arr) {
    std::unordered_map<int, int> firstSeen;
    int res = -1, lastIdx = -1;
    
    for (int i = 0; i < arr.size(); i++) {
        if (firstSeen.count(arr[i])) {
            if (i > lastIdx) {
                lastIdx = i;
                res = arr[i];
            }
        } else {
            firstSeen[arr[i]] = i;
        }
    }
    return res;
}

int main() {
    std::vector<int> v = {1, 5, 3, 4, 3, 5, 6};
    std::cout << "Last repeating: " << lastRepeating(v) << std::endl;
    return 0;
}
```
