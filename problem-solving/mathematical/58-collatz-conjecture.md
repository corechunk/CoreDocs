# 58 | Collatz Conjecture (3n + 1)

The "simplest" impossible problem in math.

---

## 1. The Objective
Take any positive integer $n$:
1. If $n$ is even, divide it by 2 ($n/2$).
2. If $n$ is odd, multiply by 3 and add 1 ($3n + 1$).
3. Repeat. 
**Conjecture:** You will always eventually hit **1**.

- **Example (n=6):** $6 \to 3 \to 10 \to 5 \to 16 \to 8 \to 4 \to 2 \to 1$.

---

## 2. Visual Logic
### The "Hailstone" Path
The numbers go up and down like hailstones in a cloud before falling to earth (1).

---

## 3. The "Aha!" Moment
This is a perfect example of a `while (n != 1)` loop. It demonstrates how simple rules can create complex, unpredictable behavior.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Iterative Simulation
 */
void printCollatz(long long n) {
    std::cout << "Sequence: " << n;
    int steps = 0;
    
    while (n != 1) {
        if (n % 2 == 0) {
            n = n / 2;
        } else {
            n = 3 * n + 1;
        }
        std::cout << " -> " << n;
        steps++;
    }
    std::cout << "\nReached 1 in " << steps << " steps." << std::endl;
}

int main() {
    long long start;
    std::cout << "Enter starting number: ";
    std::cin >> start;
    printCollatz(start);
    return 0;
}
```
