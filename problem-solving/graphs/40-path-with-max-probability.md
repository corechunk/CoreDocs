# 40 | Path with Maximum Probability

Find the "Safest" path between two nodes.

---

## 1. The Objective
Given probabilities $[0, 1]$ on edges, find the path with the highest product of probabilities.

---

## 2. Visual Logic
### The "Inverted Dijkstra"
Instead of `dist[U] + weight < dist[V]`, use:
`prob[V] = max(prob[V], prob[U] * weight_UV)`.

---

## 3. The "Aha!" Moment
Multiplying probabilities is like adding logarithms. This is a greedy optimization problem perfectly suited for a max-priority-queue.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <queue>

double maxProbability(int n, std::vector<std::vector<std::pair<int, double>>>& adj, int start, int end) {
    std::vector<double> probs(n, 0.0);
    probs[start] = 1.0;
    std::priority_queue<std::pair<double, int>> pq;
    pq.push({1.0, start});
    
    while(!pq.empty()) {
        // Standard Dijkstra logic with multiplication
    }
    return probs[end];
}
```
