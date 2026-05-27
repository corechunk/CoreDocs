# 🔍 Searching Algorithms (Finding Data)

## 1. The Objective
Searching is the process of finding the location of a specific "Target" value within a collection of data. It is a fundamental operation that determines the performance of many higher-level systems (Databases, Search Engines).

---

## 2. Visual Logic
### The Search Space
```text
Array: [ 10 | 20 | 30 | 40 | 50 ]
Target: 40
Result: Index 3
```

---

## 3. The "Aha!" Moment
- **Sorted vs. Unsorted:** The performance of a search depends heavily on whether the data is sorted. If it's unsorted, you must check everything ($O(n)$). If it's sorted, you can skip most of it ($O(\log n)$).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Abstract Search)

```cpp
#include <iostream>
#include <vector>

/**
 * Basic Linear Search as a baseline.
 */
int linearSearch(const std::vector<int>& arr, int target) {
    for (int i = 0; i < arr.size(); i++) {
        if (arr[i] == target) return i;
    }
    return -1;
}

int main() {
    std::vector<int> data = {10, 50, 30, 40, 20};
    int target = 30;
    
    int result = linearSearch(data, target);
    std::cout << "Target " << target << " found at index: " << result << std::endl;
    
    return 0;
}
```

---

## 🔗 Sub-Topics (Specific Search Strategies)
- [Linear Search](linear-search.md) - Simple, sequential check.
- [Binary Search](binary-search.md) - Efficient divide & conquer for sorted data.
- [Binary Search on Answer](binary-search-on-answer.md) - Optimization technique.

[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
