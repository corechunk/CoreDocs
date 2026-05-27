# 🎯 Binary Search

## 1. The Objective
Binary Search is an efficient algorithm for finding an item from a **sorted** list of items. It works by repeatedly dividing in half the portion of the list that could contain the item, until you've narrowed down the possible locations to just one.

---

## 2. Visual Logic
### The "Halving" Process (Target = 7)
```text
[ 1 | 3 | 5 | 7 | 9 | 11 | 13 ]  (Mid = 7, Found!)
  L           M             R
```

### Steps
1. Compare `target` with the `middle` element.
2. If `target == middle`, return index.
3. If `target < middle`, search the left half.
4. If `target > middle`, search the right half.

---

## 3. The "Aha!" Moment
- **The Logarithmic Power:** In just 32 guesses, you can find any number in a sorted list of 4 billion items ($2^{32}$).
- **The Condition:** Binary Search **ONLY** works on sorted data (or data with a monotonic property).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Iterative)

```cpp
#include <iostream>
#include <vector>

int binarySearch(const std::vector<int>& arr, int target) {
    int left = 0, right = arr.size() - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2; // Avoid overflow
        
        if (arr[mid] == target) return mid;
        if (arr[mid] < target) left = mid + 1;
        else right = mid - 1;
    }
    return -1;
}

int main() {
    std::vector<int> sortedData = {1, 3, 5, 7, 9, 11, 13};
    int target = 7;
    
    int result = binarySearch(sortedData, target);
    if (result != -1)
        std::cout << "Element found at index: " << result << std::endl;
    else
        std::cout << "Element not found." << std::endl;
        
    return 0;
}
```

---
[➔ Back to Search Hub](searching.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
