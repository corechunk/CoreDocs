# 44 | Sparse Data Mapping

Efficiently map massive IDs to a small internal index.

---

## 1. The Objective
Map large, non-contiguous IDs (like `1000234, 9999999`) to local IDs `0, 1, 2...` for array storage.

---

## 2. Visual Logic
### The "Renaming" Strategy
1. Input: `[500, 100, 500, 200]`.
2. Map:
   - `100 -> 0`
   - `200 -> 1`
   - `500 -> 2`
3. Output: `[2, 0, 2, 1]`.

---

## 3. The "Aha!" Moment
This technique, known as **Coordinate Compression**, allows you to use memory-efficient arrays even when your raw data values are huge.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <map>

void compressIDs(const std::vector<int>& ids) {
    std::map<int, int> mapper;
    for (int id : ids) mapper[id] = 0; // Just register keys
    
    int rank = 0;
    for (auto &pair : mapper) {
        pair.second = rank++;
    }
    
    std::cout << "Mapped IDs: ";
    for (int id : ids) std::cout << mapper[id] << " ";
    std::cout << std::endl;
}

int main() {
    compressIDs({9000, 100, 5555, 100});
    return 0;
}
```
