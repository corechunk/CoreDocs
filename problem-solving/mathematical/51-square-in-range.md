# 51 | Square Numbers in a Range

Find all perfect squares between two limits $L$ and $R$.

---

## 1. The Objective
Given `L = 10` and `R = 50`, return `16, 25, 36, 49`.
A perfect square is an integer that is the square of an integer.

---

## 2. Visual Logic
### The "Root Search" Strategy
Instead of checking every number from $L$ to $R$, find the square root of $L$.
- $\sqrt{10} \approx 3.16$. First integer root is 4.
- $\sqrt{50} \approx 7.07$. Last integer root is 7.
- Just square numbers from 4 to 7: $4^2, 5^2, 6^2, 7^2$.

---

## 3. The "Aha!" Moment
Efficiency matters! Checking $R-L$ numbers with `sqrt()` is slow. Finding the start and end roots and squaring them is $O(\sqrt{R})$, which is much faster.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <cmath>

/**
 * Strategy: Root-based Iteration
 */
void printSquaresInRange(int L, int R) {
    // Find the starting root
    int start = ceil(sqrt(L));
    // Find the ending root
    int end = floor(sqrt(R));
    
    std::cout << "Squares between " << L << " and " << R << ": ";
    for (int i = start; i <= end; i++) {
        std::cout << (i * i) << " ";
    }
    std::cout << std::endl;
}

int main() {
    printSquaresInRange(10, 100);
    return 0;
}
```
