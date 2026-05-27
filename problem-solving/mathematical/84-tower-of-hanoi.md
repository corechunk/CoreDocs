# 84 | Tower of Hanoi (Math Logic)

Calculate the minimum moves required for the Tower of Hanoi.

---

## 1. The Objective
Move $n$ disks from one rod to another following two rules:
1. Only one disk can be moved at a time.
2. A larger disk cannot be placed on a smaller one.

How many moves are required for $n$ disks?

---

## 2. Visual Logic
### The Recursive Pattern
To move $n$ disks:
1. Move $n-1$ disks to the helper rod. (Moves: $M_{n-1}$)
2. Move the largest disk to the target. (Moves: 1)
3. Move the $n-1$ disks from helper to target. (Moves: $M_{n-1}$)
**Total:** $2 \times M_{n-1} + 1$.

- $n=1 \to 1$
- $n=2 \to 2(1) + 1 = 3$
- $n=3 \to 2(3) + 1 = 7$

---

## 3. The "Aha!" Moment
The pattern follows $2^n - 1$.
This is the same as the **Mersenne Number** sequence!

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <cmath>

/**
 * Strategy A: Recursive Simulation (To see moves)
 */
void solveHanoi(int n, char from, char to, char aux) {
    if (n == 0) return;
    solveHanoi(n - 1, from, aux, to);
    std::cout << "Move disk " << n << " from " << from << " to " << to << std::endl;
    solveHanoi(n - 1, aux, to, from);
}

/**
 * Strategy B: Mathematical formula (To get count)
 */
long long minMoves(int n) {
    return (1LL << n) - 1;
}

int main() {
    int n = 3;
    std::cout << "Solving for " << n << " disks:" << std::endl;
    solveHanoi(n, 'A', 'C', 'B');
    std::cout << "Total moves: " << minMoves(n) << std::endl;
    return 0;
}
```
