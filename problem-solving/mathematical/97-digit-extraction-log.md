# 97 | Digit Extraction using Logarithms

Find the first digit and total digits without loops.

---

## 1. The Objective
Given `5678`, return `5` (first digit) and `4` (count) using pure math.

---

## 2. Visual Logic
### The Power of Log10
The base-10 logarithm tells you the power of 10 needed to reach a number.
- $\log_{10}(5678) \approx 3.75$.
- Number of digits = $\lfloor 3.75 \rfloor + 1 = 4$.
- First digit = $\lfloor \frac{5678}{10^{4-1}} \rfloor = \lfloor 5.678 \rfloor = 5$.

---

## 3. The "Aha!" Moment
Loops are for counting; logarithms are for "measuring." This $O(1)$ method is the most efficient way to probe the structure of a number.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <cmath>

/**
 * Strategy: Logarithmic Probing
 */
void extractInfo(long long n) {
    if (n == 0) {
        std::cout << "Digits: 1, First Digit: 0" << std::endl;
        return;
    }
    
    double logVal = log10(std::abs(n));
    int count = floor(logVal) + 1;
    
    // First digit: n / 10^(count-1)
    int firstDigit = n / pow(10, count - 1);
    
    std::cout << "Number: " << n << std::endl;
    std::cout << "Total Digits: " << count << std::endl;
    std::cout << "First Digit: " << firstDigit << std::endl;
}

int main() {
    extractInfo(987654);
    return 0;
}
```
