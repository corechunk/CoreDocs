# 📊 Complexity Analysis

## 1. The Objective
Complexity Analysis is the mathematical framework for comparing algorithms. It measures how the **Time** (execution speed) and **Space** (memory usage) requirements of an algorithm grow as the **Input Size (n)** increases.

---

## 2. Visual Logic
### The Growth Hierarchy
```text
(Fastest) O(1) < O(log n) < O(n) < O(n log n) < O(n²) < O(2ⁿ) (Slowest)
```

### Amortized Cost (The "Spike")
```text
Op 1: [x] (1)
Op 2: [x] (1)
Op 3: [x] (1)
Op 4: [x|x|x|x|y] (N) <-- Resize!
Result: (1+1+1+N) / 4 ≈ O(1)
```

---

## 3. The Logic Bridge
- **Asymptotic Thinking:** In DSA, we don't care about the difference between 10ms and 20ms. we care about what happens when $n$ goes from 1,000 to 1,000,000.
- **Dropping Constants:** $O(2N + 100)$ is just $O(N)$ because the growth rate is linear. 
- **Standard of Comparison:** We always default to **Worst Case (Big O)** because it provides a reliable guarantee that the system won't crash or hang under pressure.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Measuring Loops)

```cpp
#include <iostream>
#include <vector>

// O(n) - Linear Time
void printAll(const std::vector<int>& arr) {
    for (int x : arr) std::cout << x << " ";
}

// O(n^2) - Quadratic Time
void printPairs(const std::vector<int>& arr) {
    for (int x : arr) {
        for (int y : arr) std::cout << "(" << x << "," << y << ") ";
    }
}

int main() {
    std::vector<int> data = {1, 2, 3};
    std::cout << "O(n):\n"; printAll(data);
    std::cout << "\nO(n^2):\n"; printPairs(data);
    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
