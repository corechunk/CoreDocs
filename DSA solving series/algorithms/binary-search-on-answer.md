# 🎯 Binary Search on Answer

## 1. The Objective
Binary Search on Answer is a powerful optimization technique used to solve "Min-Max" or "Max-Min" problems. Instead of searching for an element in an array, we search for the **minimal possible answer** that satisfies a certain condition.

---

## 2. Visual Logic
### The Monotonic Property
To use this, the condition must be monotonic (e.g., if a speed of 5km/h works, then 6km/h, 7km/h... also work).
```text
Speed:   [ 1 | 2 | 3 | 4 | 5 | 6 | 7 ]
Works?:  [ F | F | F | T | T | T | T ]
                       ^ (Our Target: Min speed that works)
```

---

## 3. The Logic Bridge
- **The "Check" Function:** The heart of this technique is a `bool check(value)` function. It tells us if a specific candidate answer is "Possible". 
- **Space Reduction:** Instead of trying every value from $1$ to $10^9$ ($O(N)$), we binary search through the range of possible answers ($O(\log(\text{Range}) \times \text{cost of check})$).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Abstract Example)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

// A condition function (e.g., Can we finish work in 'val' hours?)
bool isPossible(int val, const std::vector<int>& tasks, int limit) {
    int count = 0;
    for (int t : tasks) {
        count += (t + val - 1) / val; // Example logic
    }
    return count <= limit;
}

int solve(const std::vector<int>& tasks, int limit) {
    int low = 1, high = 1e9; // Range of possible answers
    int ans = high;

    while (low <= high) {
        int mid = low + (high - low) / 2;
        if (isPossible(mid, tasks, limit)) {
            ans = mid;    // It works! Try to find a smaller (better) answer
            high = mid - 1;
        } else {
            low = mid + 1; // Doesn't work, we need a larger value
        }
    }
    return ans;
}

int main() {
    std::vector<int> tasks = {10, 20, 30};
    int limit = 5;
    std::cout << "Optimal Answer: " << solve(tasks, limit) << std::endl;
    return 0;
}
```

---
[➔ Back to Search Hub](searching.md) | [➔ Back to Roadmap](../DSA-Master-Roadmap.md)
