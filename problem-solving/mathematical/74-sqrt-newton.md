# 74 | Square Root (Newton-Raphson)

Calculate precise square roots using calculus.

---

## 1. The Objective
Find $\sqrt{n}$ with decimal precision using an iterative approximation method.

---

## 2. Visual Logic
### The "Guess and Refine" Method
Start with a guess $x$. If $x$ is not the root, the average of $x$ and $n/x$ will be a much better guess.
1. `n = 2, guess = 1`
2. `next = (1 + 2/1) / 2 = 1.5`
3. `next = (1.5 + 2/1.5) / 2 = 1.416...`
4. `next = (1.416 + 2/1.416) / 2 = 1.4142...`

---

## 3. The "Aha!" Moment
The formula $x_{next} = \frac{1}{2} (x + \frac{n}{x})$ converges to the square root incredibly fast (quadratically). Usually, 10 iterations are enough for any standard number.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <iomanip>

/**
 * Strategy: Newton-Raphson Iteration
 * Efficiency: High Precision, Few Steps
 */
double newtonSqrt(double n) {
    if (n < 0) return -1;
    if (n == 0) return 0;
    
    double x = n; // Initial guess
    double root;
    
    while (true) {
        root = 0.5 * (x + (n / x));
        
        // Stop when the difference is tiny
        if (std::abs(root - x) < 0.0000001) {
            break;
        }
        x = root;
    }
    return root;
}

int main() {
    double n = 2;
    std::cout << "Precise sqrt of " << n << " is: " << std::fixed << std::setprecision(10) << newtonSqrt(n) << std::endl;
    return 0;
}
```
