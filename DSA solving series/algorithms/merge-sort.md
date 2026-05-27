# 🌊 Merge Sort

## 1. The Objective
Merge Sort is a **Divide and Conquer** algorithm. It divides the input array into two halves, calls itself for the two halves, and then merges the two sorted halves.

---

## 2. Visual Logic
### Divide & Conquer (n=4)
1. **Divide:** `[5, 1, 4, 2]` -> `[5, 1]` and `[4, 2]`
2. **Conquer:** `[5, 1]` -> `[1, 5]` and `[4, 2]` -> `[2, 4]`
3. **Merge:** `[1, 5]` and `[2, 4]` -> `[1, 2, 4, 5]`

---

## 3. The "Aha!" Moment
- **Stability:** Merge Sort is stable, making it a favorite for sorting complex objects.
- **Guarantee:** Unlike Quick Sort, Merge Sort **guarantees** $O(n \log n)$ time even in the worst case.
- **Space Tradeoff:** It requires $O(n)$ extra space to store the temporary merged arrays.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

void merge(std::vector<int>& arr, int l, int m, int r) {
    int n1 = m - l + 1;
    int n2 = r - m;
    std::vector<int> L(n1), R(n2);
    for (int i = 0; i < n1; i++) L[i] = arr[l + i];
    for (int j = 0; j < n2; j++) R[j] = arr[m + 1 + j];

    int i = 0, j = 0, k = l;
    while (i < n1 && j < n2) {
        if (L[i] <= R[j]) arr[k++] = L[i++];
        else arr[k++] = R[j++];
    }
    while (i < n1) arr[k++] = L[i++];
    while (j < n2) arr[k++] = R[j++];
}

void mergeSort(std::vector<int>& arr, int l, int r) {
    if (l < r) {
        int m = l + (r - l) / 2;
        mergeSort(arr, l, m);
        mergeSort(arr, m + 1, r);
        merge(arr, l, m, r);
    }
}

int main() {
    std::vector<int> data = {5, 1, 4, 2, 8};
    mergeSort(data, 0, data.size() - 1);
    for (int x : data) std::cout << x << " ";
    return 0;
}
```

---
[➔ Back to Sorting Hub](sorting.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
