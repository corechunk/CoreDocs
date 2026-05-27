# 98 | Monte Carlo Method (PI Estimation)

Estimate the value of $\pi$ using probability.

---

## 1. The Objective
Estimate $\pi$ by "throwing darts" at a square containing a circle.

---

## 2. Visual Logic
### The Circle in a Square
1. Square Area: $2 \times 2 = 4$.
2. Circle Area: $\pi \times 1^2 = \pi$.
3. Ratio: $\frac{\text{Circle}}{\text{Square}} = \frac{\pi}{4}$.
4. Therefore: $\pi = 4 \times \frac{\text{Points Inside Circle}}{\text{Total Points}}$.

---

## 3. The "Aha!" Moment
A point $(x, y)$ is inside the circle if $x^2 + y^2 \le 1$. By generating thousands of random coordinates, the law of large numbers will reveal the value of $\pi$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <cstdlib>
#include <ctime>

/**
 * Strategy: Stochastic Simulation
 */
double estimatePi(int totalPoints) {
    int insideCircle = 0;
    
    for (int i = 0; i < totalPoints; i++) {
        // Random x, y between 0 and 1
        double x = (double)rand() / RAND_MAX;
        double y = (double)rand() / RAND_MAX;
        
        if (x*x + y*y <= 1.0) {
            insideCircle++;
        }
    }
    
    return 4.0 * insideCircle / totalPoints;
}

int main() {
    srand(time(0));
    int n = 1000000;
    std::cout << "Estimated PI after " << n << " samples: " << estimatePi(n) << std::endl;
    return 0;
}
```
