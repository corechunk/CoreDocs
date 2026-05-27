# 85 | Josephus Problem

The deadly game of elimination.

---

## 1. The Objective
$n$ people stand in a circle. Starting from the first, every $k^{th}$ person is eliminated until only one remains. Find the position of the survivor.
- **Example:** $n=5, k=2$.
- People: 1, 2, 3, 4, 5
- 2 is out. (Left: 1, 3, 4, 5)
- 4 is out. (Left: 1, 3, 5)
- 1 is out. (Left: 3, 5)
- 5 is out. (Survivor: **3**)

---

## 2. Visual Logic
### The Recursive Bridge
$J(n, k) = (J(n-1, k) + k) \pmod n$
The survivor position in a circle of $n$ is just the survivor position of $n-1$ shifted by $k$.

---

## 3. The "Aha!" Moment
For $k=2$, there is a beautiful binary trick:
1. Write $n$ in binary.
2. Move the first bit to the end.
3. The result is the survivor position!
- $n=5$ (Binary `101`) $\to$ Move `1` to end $\to$ `011` (Binary `3`).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy A: Recursive Formula
 * Efficiency: Time O(n)
 */
int josephus(int n, int k) {
    if (n == 1) return 1;
    // +1 to convert from 0-indexed to 1-indexed
    return (josephus(n - 1, k) + k - 1) % n + 1;
}

/**
 * Strategy B: Iterative (Prevents Stack Overflow)
 */
int josephusIterative(int n, int k) {
    int res = 0; // 0-indexed result
    for (int i = 1; i <= n; i++) {
        res = (res + k) % i;
    }
    return res + 1;
}

int main() {
    int n = 5, k = 2;
    std::cout << "Survivor position: " << josephusIterative(n, k) << std::endl;
    return 0;
}
```
