# 92 | Standard Deviation

Measure the spread of data.

---

## 1. The Objective
Calculate how much the values in a set differ from the mean.
$\sigma = \sqrt{\frac{\sum (x_i - \mu)^2}{N}}$

---

## 2. Visual Logic
### The 3-Step Process
1. Find the **Mean** ($\mu$).
2. For each number, find the **Square of its distance** from the mean: $(x - \mu)^2$.
3. Find the average of those squares and take the **Square Root**.

---

## 3. The "Aha!" Moment
Standard deviation tells you if your data is "consistent" (low $\sigma$) or "scattered" (high $\sigma$). In code, this is two loops: one for mean, one for variance.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <cmath>
#include <numeric>

/**
 * Strategy: Multi-pass accumulation
 */
double calculateSD(const std::vector<double>& data) {
    int n = data.size();
    if (n == 0) return 0;
    
    double mean = std::accumulate(data.begin(), data.end(), 0.0) / n;
    
    double variance = 0;
    for (double x : data) {
        variance += pow(x - mean, 2);
    }
    variance /= n;
    
    return sqrt(variance);
}

int main() {
    std::vector<double> v = {10, 12, 23, 23, 16, 23, 21, 16};
    std::cout << "Standard Deviation: " << calculateSD(v) << std::endl;
    return 0;
}
```
