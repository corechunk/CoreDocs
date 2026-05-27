# 93 | Simple Linear Regression

Predict $y$ based on $x$ using the line $y = mx + c$.

---

## 1. The Objective
Find the line that "best fits" a set of $(x, y)$ points by minimizing the error.

---

## 2. Visual Logic
### The "Slope and Intercept"
$m = \frac{N\sum(xy) - \sum x \sum y}{N\sum(x^2) - (\sum x)^2}$
$c = \frac{\sum y - m\sum x}{N}$

---

## 3. The "Aha!" Moment
Linear regression is the "Hello World" of **Machine Learning**. It reduces a scatter plot into a single mathematical relationship.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

/**
 * Strategy: Least Squares Method
 */
void linearRegression(const std::vector<double>& x, const std::vector<double>& y) {
    int n = x.size();
    double sumX=0, sumY=0, sumXY=0, sumX2=0;
    
    for(int i=0; i<n; i++) {
        sumX += x[i];
        sumY += y[i];
        sumXY += x[i] * y[i];
        sumX2 += x[i] * x[i];
    }
    
    double m = (n * sumXY - sumX * sumY) / (n * sumX2 - sumX * sumX);
    double c = (sumY - m * sumX) / n;
    
    std::cout << "Best fit line: y = " << m << "x + " << c << std::endl;
}

int main() {
    std::vector<double> x = {1, 2, 3, 4, 5};
    std::vector<double> y = {2, 4, 5, 4, 5};
    linearRegression(x, y);
    return 0;
}
```
