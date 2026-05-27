# 29 | First Non-Repeating (HashMap Version)

Optimized search for the first unique item.

---

## 1. The Objective
Find the first item that doesn't repeat using the $O(n)$ mapping strategy.

---

## 2. Visual Logic
Same as Problem 11 (Strings), but applying it to a generic integer array.

---

## 3. The "Aha!" Moment
Using `unordered_map` handles any integer value, not just ASCII 0-255.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

int firstUnique(const std::vector<int>& arr) {
    std::unordered_map<int, int> freq;
    for (int x : arr) freq[x]++;
    
    for (int x : arr) {
        if (freq[x] == 1) return x;
    }
    return -1;
}

int main() {
    std::vector<int> v = {9, 4, 9, 6, 7, 4};
    std::cout << "First unique: " << firstUnique(v) << std::endl;
    return 0;
}
```
