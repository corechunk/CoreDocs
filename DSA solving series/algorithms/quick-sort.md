# ⚡ Quick Sort

## 1. The Objective
Quick Sort is a highly efficient, in-place sorting algorithm that uses a **Pivot** to partition the array into two sub-arrays (elements smaller than pivot and elements larger than pivot).

---

## 2. Visual Logic
### Partitioning (Pivot = Last Element)
```text
[ 5 | 1 | 8 | 2 | 4 ]  Pivot = 4
[ 1 | 2 ] < [ 4 ] < [ 5 | 8 ]
```
- The pivot `4` is now in its correct sorted position.

---

## 3. The "Aha!" Moment
- **In-Place Speed:** Because it sorts "in-place" (using a small recursion stack), it has better cache locality than Merge Sort, making it faster in practice for many datasets.
- **The Achilles' Heel:** Without a good pivot selection (like randomized pivot), Quick Sort can degrade to $O(n^2)$ if the data is already sorted.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Lomuto Partition)

```cpp
#include <iostream>
#include <vector>

int partition(std::vector<int>& arr, int low, int high) {
    int pivot = arr[high];
    int i = low - 1;
    for (int j = low; j < high; j++) {
        if (arr[j] < pivot) std::swap(arr[++i], arr[j]);
    }
    std::swap(arr[i + 1], arr[high]);
    return i + 1;
}

void quickSort(std::vector<int>& arr, int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

int main() {
    std::vector<int> data = {5, 1, 8, 2, 4};
    quickSort(data, 0, data.size() - 1);
    for (int x : data) std::cout << x << " ";
    return 0;
}
```

---
[➔ Back to Sorting Hub](sorting.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
