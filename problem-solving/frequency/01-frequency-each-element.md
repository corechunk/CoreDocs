# 01 | Frequency of Each Element

Count the occurrences of every unique item in an array.

---

## 1. The Objective
Given an array `[1, 2, 2, 3, 3, 3]`, return:
`1: 1 time, 2: 2 times, 3: 3 times`.

---

## 2. Visual Logic
### The "Counter" Strategy
Create a mapping where the **Element** is the key and the **Count** is the value.
```text
Array: [A, B, A, C, B, A]
Map:
A -> 1+1+1 = 3
B -> 1+1   = 2
C -> 1     = 1
```

---

## 3. The "Aha!" Moment
Instead of nested loops ($O(n^2)$), a single pass through the array with a `std::unordered_map` solves this in $O(n)$ time.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_map>

/**
 * Strategy: HashMap Counting
 * Efficiency: Time O(n), Space O(u) where u is unique elements
 */
void printFrequency(const std::vector<int>& arr) {
    std::unordered_map<int, int> freq;
    
    // Fill the map
    for (int x : arr) {
        freq[x]++;
    }
    
    // Print the results
    for (auto const& [val, count] : freq) {
        std::cout << val << " appears " << count << " times" << std::endl;
    }
}

int main() {
    std::vector<int> v = {10, 20, 20, 10, 10, 20, 5, 20};
    printFrequency(v);
    return 0;
}
```
