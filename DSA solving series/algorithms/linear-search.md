# 📏 Linear Search

## 1. The Objective
Linear Search (or Sequential Search) is the most basic search algorithm. It checks every element in a collection one by one until the target is found or the end is reached.

---

## 2. Visual Logic
### The Step-by-Step Check (Target = 40)
```text
[ 10 | 50 | 30 | 40 | 20 ]
  ^ (No)
       ^ (No)
            ^ (No)
                 ^ (YES!)
```

---

## 3. The "Aha!" Moment
- **Worst-Case Necessity:** If the data is completely unsorted and you have no other information, Linear Search is the best (and only) you can do.
- **Small Data Wins:** For very small arrays (e.g., < 10 elements), Linear Search can sometimes be faster than Binary Search due to less overhead (no middle calculation/branching).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

int linearSearch(const std::vector<int>& arr, int target) {
    for (int i = 0; i < arr.size(); i++) {
        if (arr[i] == target) return i;
    }
    return -1;
}

int main() {
    std::vector<int> data = {10, 50, 30, 40, 20};
    int target = 40;
    
    int result = linearSearch(data, target);
    std::cout << "Target found at index: " << result << std::endl;
    
    return 0;
}
```

---
[➔ Back to Search Hub](searching.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
