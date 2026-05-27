# 🚀 Non-Comparison Sorts (Linear Time)

## 1. The Objective
Comparison-based sorts (Merge, Quick, Heap) have a theoretical limit of $O(n \log n)$. **Non-Comparison Sorts** (Counting, Radix) can achieve **$O(n)$** time complexity by exploiting properties of the data (like fixed ranges or integer keys).

---

## 2. Visual Logic
### Counting Sort (Range 0-5)
```text
Input: [ 1, 4, 1, 2, 5 ]
Count Array: [ 0:0, 1:2, 2:1, 3:0, 4:1, 5:1 ]
Result: [ 1, 1, 2, 4, 5 ]
```
- We don't compare elements; we count occurrences and calculate positions.

---

## 3. The Logic Bridge
- **The "Cheat" Code:** These algorithms "cheat" the $n \log n$ limit by using **Index-as-Value**. 
- **The Cost:** They require extra memory proportional to the **range** of values. Counting Sort is amazing for sorting 1 million exam scores (range 0-100) but terrible for sorting 1 million random 64-bit integers.
- **Radix Sort:** Breaks numbers into digits and uses Counting Sort on each digit, allowing linear time for larger numbers.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Counting Sort)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

void countingSort(std::vector<int>& arr) {
    if (arr.empty()) return;
    int maxVal = *std::max_element(arr.begin(), arr.end());
    std::vector<int> count(maxVal + 1, 0);

    for (int x : arr) count[x]++;
    
    int idx = 0;
    for (int i = 0; i <= maxVal; i++) {
        while (count[i]-- > 0) arr[idx++] = i;
    }
}

int main() {
    std::vector<int> data = {4, 2, 2, 8, 3, 3, 1};
    countingSort(data);
    for (int x : data) std::cout << x << " ";
    return 0;
}
```

---
[➔ Back to Sorting Hub](sorting.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
