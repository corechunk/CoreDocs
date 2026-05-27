# 50 | Mode of Stream Data (Conceptual)

Track the most frequent element as data arrives one-by-one.

---

## 1. The Objective
Implement a system that accepts a stream of integers and can return the current mode in $O(1)$ time.

---

## 2. Visual Logic
### The "Live Leaderboard"
1. `freqMap`: `Value -> Count`.
2. `maxFreq`: Current highest count.
3. `mode`: Current winner.
As each number `x` arrives:
- `freqMap[x]++`
- If `freqMap[x] > maxFreq`: update `maxFreq` and `mode`.

---

## 3. The "Aha!" Moment
Mapping doesn't just work on static arrays; it’s the standard way to monitor **Real-time Systems** (like trending topics on social media or top-selling products).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <unordered_map>

class StreamMode {
    std::unordered_map<int, int> freq;
    int maxFreq = 0;
    int currentMode = -1;

public:
    void add(int x) {
        freq[x]++;
        if (freq[x] > maxFreq) {
            maxFreq = freq[x];
            currentMode = x;
        }
        std::cout << "Streamed: " << x << " | Mode: " << currentMode << std::endl;
    }
};

int main() {
    StreamMode sm;
    sm.add(1); sm.add(2); sm.add(2); sm.add(3); sm.add(1); sm.add(1);
    return 0;
}
```
