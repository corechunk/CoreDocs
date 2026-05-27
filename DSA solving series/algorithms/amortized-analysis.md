# 📉 Amortized Analysis

## 1. The Objective
Amortized analysis is used to find the **average cost per operation** over a worst-case sequence of operations. It provides a more realistic view of performance for data structures where most operations are cheap, but an occasional one is expensive.

---

## 2. Visual Logic
### The "Spike" (Dynamic Array)
```text
Push 1: [x] (1)
Push 2: [x] (1)
Push 3: [x] (1)
Push 4: [x|x|x|x] (N) <-- Resize & Copy
Total Cost: (1+1+1+N) / 4 ≈ Constant
```

---

## 3. The Logic Bridge
- **The "Banker's" Analogy:** Imagine you save $1 every day (cheap operations) to pay for a $30 bill at the end of the month (expensive operation). On average, your cost is $1/day. 
- **Why it matters:** If we only used Big O (Worst Case), we'd say `std::vector::push_back` is $O(n)$. But in reality, it behaves like $O(1)$. Amortized analysis proves this.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Abstract Simulation)

```cpp
#include <iostream>

void simulatePush(int n) {
    int total_cost = 0;
    int capacity = 1;
    
    for (int i = 1; i <= n; i++) {
        if (i > capacity) {
            capacity *= 2;
            total_cost += i; // Resize cost
            std::cout << "Push " << i << ": Resize Spike! (Cost: " << i << ")\n";
        } else {
            total_cost += 1; // Normal cost
        }
    }
    std::cout << "Average Cost: " << (double)total_cost / n << std::endl;
}

int main() {
    simulatePush(100);
    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
