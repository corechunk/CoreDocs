# 🍪 Greedy Algorithms

## 1. The Objective
A Greedy algorithm is an approach that builds up a solution piece by piece, always choosing the next piece that offers the **most immediate (local) benefit**. It makes the choice that seems best at that moment without considering future consequences.

---

## 2. Visual Logic
### The Local Choice
```text
Target: 36 cents (Coin Change)
Coins: [ 25, 10, 5, 1 ]

1. Pick 25 (Remaining: 11)
2. Pick 10 (Remaining: 1)
3. Pick 1  (Remaining: 0)
Result: 3 coins.
```

---

## 3. The Logic Bridge
- **The "Greedy Property":** A greedy choice only works if a local optimal choice leads to a global optimal solution. This is true for things like **Fractional Knapsack** or **Dijkstra**, but false for **0/1 Knapsack**.
- **Efficiency:** Greedy algorithms are usually very fast ($O(n \log n)$ due to sorting or $O(n)$) because they never backtrack or re-evaluate previous decisions.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Activity Selection)

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

struct Activity {
    int start, end;
};

bool compare(Activity a, Activity b) { return a.end < b.end; }

void selectActivities(std::vector<Activity>& acts) {
    std::sort(acts.begin(), acts.end(), compare);
    
    int last_end = -1;
    for (auto a : acts) {
        if (a.start >= last_end) {
            std::cout << "Activity: " << a.start << "-" << a.end << "\n";
            last_end = a.end;
        }
    }
}

int main() {
    std::vector<Activity> acts = {{1, 4}, {3, 5}, {0, 6}, {5, 7}, {3, 9}, {5, 9}, {6, 10}, {8, 11}};
    selectActivities(acts);
    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
