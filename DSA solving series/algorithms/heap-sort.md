# 🏔️ Heap Sort

## 1. The Objective
Heap Sort is a comparison-based sorting technique based on the **Binary Heap** data structure. It is similar to selection sort where we first find the maximum element and place it at the end. We repeat the same process for the remaining elements.

---

## 2. Visual Logic
### Two-Step Process
1. **Build Max-Heap:** Transform the unsorted array into a heap where `Root > Children`.
2. **Extract & Heapify:** Swap the root (max) with the last element, reduce heap size, and "Heapify" the root to restore heap property.

---

## 3. The Logic Bridge
- **Worst-Case Reliability:** Unlike Quick Sort (which can hit $O(n^2)$), Heap Sort is **guaranteed** $O(n \log n)$ in all cases.
- **Memory Efficiency:** It is an **in-place** algorithm ($O(1)$ extra space), unlike Merge Sort which needs $O(n)$. 
- **The "Unstable" Catch:** Heap Sort is not stable; the relative order of equal elements may change.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void heapify(std::vector<int>& arr, int n, int i) {
    int largest = i;
    int l = 2 * i + 1;
    int r = 2 * i + 2;

    if (l < n && arr[l] > arr[largest]) largest = l;
    if (r < n && arr[r] > arr[largest]) largest = r;

    if (largest != i) {
        std::swap(arr[i], arr[largest]);
        heapify(arr, n, largest);
    }
}

void heapSort(std::vector<int>& arr) {
    int n = arr.size();
    for (int i = n / 2 - 1; i >= 0; i--) heapify(arr, n, i);
    for (int i = n - 1; i > 0; i--) {
        std::swap(arr[0], arr[i]);
        heapify(arr, i, 0);
    }
}

int main() {
    std::vector<int> data = {12, 11, 13, 5, 6, 7};
    heapSort(data);
    for (int x : data) std::cout << x << " ";
    return 0;
}
```

---
[➔ Back to Sorting Hub](sorting.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
