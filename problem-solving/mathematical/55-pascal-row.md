# 55 | Pascal's Triangle (Row)

Generate a specific row of Pascal's Triangle.

---

## 1. The Objective
Given `row = 4`, return `1, 4, 6, 4, 1`.

---

## 2. Visual Logic
### The Binomial Property
Row $n$ consists of binomial coefficients: $\binom{n}{0}, \binom{n}{1}, \dots, \binom{n}{n}$.
- Row 0: 1
- Row 1: 1 1
- Row 2: 1 2 1
- Row 3: 1 3 3 1
- Row 4: 1 4 6 4 1

---

## 3. The "Aha!" Moment
You can calculate each term from the previous one without factorials:
$\binom{n}{k} = \binom{n}{k-1} \times \frac{n-k+1}{k}$
This is $O(n)$ and avoids overflow of factorials.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

/**
 * Strategy: Linear Term Calculation
 * Efficiency: Time O(n), Space O(n)
 */
void printPascalRow(int n) {
    long long current = 1;
    std::cout << "Row " << n << ": ";
    std::cout << current << " "; // First element is always 1
    
    for (int k = 1; k <= n; k++) {
        current = current * (n - k + 1) / k;
        std::cout << current << " ";
    }
    std::cout << std::endl;
}

int main() {
    printPascalRow(4);
    printPascalRow(10);
    return 0;
}
```
