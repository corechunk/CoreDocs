# 31 | Duplicates within Distance K

Check if there are any duplicate elements within $K$ indices of each other.

---

## 1. The Objective
Given `[1, 2, 3, 1, 4]` and `K=3`, return `true` (index 0 and 3 are distance 3).

---

## 2. Visual Logic
### The "Rolling Set" Strategy
Keep a Set of the last $K$ elements. As you move forward:
1. Check if current element is in the Set.
2. If YES: Match found!
3. If NO: Add current, remove the element at index `i-K`.

---

## 3. The "Aha!" Moment
A Set with a fixed size limit acts like a "Short-term Memory." It allows you to check local duplication in $O(n)$ time.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>

bool hasNearbyDup(const std::vector<int>& arr, int k) {
    std::unordered_set<int> window;
    for (int i = 0; i < arr.size(); i++) {
        if (window.count(arr[i])) return true;
        
        window.insert(arr[i]);
        if (window.size() > k) {
            window.erase(arr[i - k]);
        }
    }
    return false;
}

int main() {
    std::vector<int> v = {1, 2, 3, 1};
    std::cout << "Nearby Dup? " << hasNearbyDup(v, 3) << std::endl;
    return 0;
}
```
