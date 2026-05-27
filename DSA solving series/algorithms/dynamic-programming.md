# 🧠 Dynamic Programming (DP)

## 1. The Objective
Dynamic Programming is an algorithmic technique for solving an optimization problem by breaking it down into simpler **overlapping subproblems** and utilizing the fact that the optimal solution to the overall problem depends upon the optimal solution to its subproblems.

---

## 2. Visual Logic
### Recursion with Overlap (Fibonacci)
```text
          fib(5)
         /      \
      fib(4)    fib(3)
     /    \      /    \
  fib(3) fib(2) fib(2) fib(1)
    ^------^------^
(Repeated calculations!)
```
- DP stores the result of `fib(3)` the first time and reuses it later.

---

## 3. The Logic Bridge
- **The "Memory" Tradeoff:** DP is essentially **Recursion + Memory**. We trade space (to store results) for massive time gains ($O(2^n) \rightarrow O(n)$).
- **Two Approaches:**
    - **Top-Down (Memoization):** Start with the big problem, solve subproblems recursively, and cache results.
    - **Bottom-Up (Tabulation):** Start with the smallest subproblems and build up to the big one using a table (loop).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation (Fibonacci Tabulation)

```cpp
#include <iostream>
#include <vector>

long long fib(int n) {
    if (n <= 1) return n;
    std::vector<long long> dp(n + 1);
    dp[0] = 0;
    dp[1] = 1;
    for (int i = 2; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    return dp[n];
}

int main() {
    int n = 50;
    std::cout << "Fibonacci of " << n << " is " << fib(n) << std::endl;
    return 0;
}
```

---
[➔ Back to Roadmap](../DSA-Master-Roadmap.md)
