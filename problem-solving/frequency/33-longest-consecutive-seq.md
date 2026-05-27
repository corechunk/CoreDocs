# 33 | Longest Consecutive Sequence

Find the length of the longest chain of consecutive numbers (e.g., 1, 2, 3).

---

## 1. The Objective
Given `[100, 4, 200, 1, 3, 2]`, return `4` (`1, 2, 3, 4`).

---

## 2. Visual Logic
### The "Anchor Search"
1. Put all numbers in a Set.
2. For each number `x`:
   - Is `x-1` in the Set?
   - If NO: `x` is the **Start** of a sequence.
   - While `x+1` is in Set: Increment length and `x`.

---

## 3. The "Aha!" Moment
By only starting from a "Sequence Start" (where $x-1$ is missing), you ensure each number is only visited a constant number of times. $O(n)$ complexity!

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <unordered_set>
#include <algorithm>

int longestConsecutive(const std::vector<int>& nums) {
    std::unordered_set<int> s(nums.begin(), nums.end());
    int longest = 0;
    
    for (int x : s) {
        if (!s.count(x - 1)) { // Start of sequence
            int curr = x;
            int streak = 1;
            while (s.count(curr + 1)) {
                curr++;
                streak++;
            }
            longest = std::max(longest, streak);
        }
    }
    return longest;
}

int main() {
    std::vector<int> v = {100, 4, 200, 1, 3, 2};
    std::cout << "Longest chain: " << longestConsecutive(v) << std::endl;
    return 0;
}
```
