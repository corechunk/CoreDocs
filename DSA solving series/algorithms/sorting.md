# 📊 Sorting Algorithms (Ordering Data)

## 1. The Objective
Sorting is the process of arranging data in a specific order (usually ascending or descending). It is one of the most studied problems in computer science because efficient sorting is key to optimizing other algorithms (like Binary Search).

---

## 2. Visual Logic
### Unsorted vs. Sorted
```text
Unsorted: [ 5 | 1 | 4 | 2 | 8 ]
Sorted:   [ 1 | 2 | 4 | 5 | 8 ]
```

---

## 3. The "Aha!" Moment
- **Stability:** A sorting algorithm is "stable" if it preserves the relative order of equal elements. This is crucial for multi-level sorting (e.g., sorting by name, then by age).
- **In-Place:** An algorithm is "in-place" if it doesn't require extra memory proportional to the size of the data ($O(1)$ extra space).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Abstract Bubble Sort)

```cpp
#include <iostream>
#include <vector>

void bubbleSort(std::vector<int>& arr) {
    int n = arr.size();
    for (int i = 0; i < n-1; i++) {
        for (int j = 0; j < n-i-1; j++) {
            if (arr[j] > arr[j+1]) std::swap(arr[j], arr[j+1]);
        }
    }
}

int main() {
    std::vector<int> data = {5, 1, 4, 2, 8};
    bubbleSort(data);
    
    std::cout << "Sorted Data: ";
    for (int x : data) std::cout << x << " ";
    std::cout << std::endl;
    
    return 0;
}
```

---

## 🔗 Sub-Topics (Specific Sorting Strategies)
- [Bubble Sort](bubble-sort.md) - Simple, exchange-based.
- [Merge Sort](merge-sort.md) - Stable, Divide & Conquer ($O(n \log n)$).
- [Quick Sort](quick-sort.md) - Fast, In-place ($O(n \log n)$ average).
- [Heap Sort](heap-sort.md) - Tree-based, constant extra space.
- [Non-Comparison Sorts](non-comparison-sorts.md) - Radix, Counting ($O(n)$).

[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
