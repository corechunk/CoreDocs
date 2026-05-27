# 19 | Missing Elements in Range

Identify which numbers from a range $[L, R]$ are NOT in the array.

---

## 1. The Objective
Given `[10, 12, 11, 15]` and range `[10, 15]`, return `[13, 14]`.

---

## 2. Visual Logic
### The "Set Checklist"
1. Put all array elements into a Set.
2. For $i$ from $L$ to $R$:
   - If $i$ is NOT in Set: Print $i$.

---

## 3. The "Aha!" Moment
The Set allows you to perform "Existence Queries" in constant time, turning a potentially slow range search into a linear pass.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>

void printMissing(const std::vector<int>& arr, int low, int high) {
    std::unordered_set<int> s(arr.begin(), arr.end());
    
    std::cout << "Missing: ";
    for (int i = low; i <= high; i++) {
        if (s.find(i) == s.end()) {
            std::cout << i << " ";
        }
    }
    std::cout << std::endl;
}

int main() {
    std::vector<int> v = {1, 3, 5, 7};
    printMissing(v, 1, 10);
    return 0;
}
```
