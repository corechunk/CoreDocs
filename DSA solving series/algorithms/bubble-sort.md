# 🧼 Bubble Sort

## 1. The Objective
Bubble Sort is the simplest sorting algorithm. It works by repeatedly stepping through the list, comparing adjacent elements and swapping them if they are in the wrong order. The pass through the list is repeated until the list is sorted.

---

## 2. Visual Logic
### The "Bubbling" Up
In each pass, the largest element "bubbles up" to its correct position at the end.
```text
Pass 1: [ 5 | 1 | 4 | 2 | 8 ]
Compare 5, 1 -> Swap: [ 1 | 5 | 4 | 2 | 8 ]
Compare 5, 4 -> Swap: [ 1 | 4 | 5 | 2 | 8 ]
...
End of Pass 1: [ 1 | 4 | 2 | 5 | 8 ] (8 is locked)
```

---

## 3. The Logic Bridge
- **Why use it?:** It's almost never used in production due to $O(n^2)$ complexity, but it's the easiest to implement and perfect for teaching the concept of "In-place swapping".
- **Early Exit Optimization:** If no swaps occur in a full pass, the array is already sorted. We can stop immediately ($O(n)$ best case).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Optimized)

```cpp
#include <iostream>
#include <vector>

void bubbleSort(std::vector<int>& arr) {
    int n = arr.size();
    bool swapped;
    for (int i = 0; i < n - 1; i++) {
        swapped = false;
        for (int j = 0; j < n - i - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                std::swap(arr[j], arr[j + 1]);
                swapped = true;
            }
        }
        if (!swapped) break; // Optimized exit
    }
}

int main() {
    std::vector<int> data = {64, 34, 25, 12, 22, 11, 90};
    bubbleSort(data);
    for (int x : data) std::cout << x << " ";
    return 0;
}
```

---
[➔ Back to Sorting Hub](sorting.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
