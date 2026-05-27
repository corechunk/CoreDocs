# 42 | Kaprekar Number

Check if the square of a number can be split into two parts that sum to the original number.

---

## 1. The Objective
A number $n$ is a **Kaprekar Number** if the representation of $n^2$ can be split into two parts (left and right) such that the sum of parts is $n$.
- **Example:** $45$.
- $45^2 = 2025$.
- Split: $20 + 25 = 45$. (Kaprekar!)
- **Example:** $297$.
- $297^2 = 88209$.
- Split: $88 + 209 = 297$. (Kaprekar!)

---

## 2. Visual Logic
### The "Sliding Split"
For a square with $D$ digits, you can split it at any position $k$. 
The right part has $k$ digits, and the left part has $(D-k)$ digits.
Sum = `(square / 10^k) + (square % 10^k)`.

---

## 3. The "Aha!" Moment
The right part **must** have the same number of digits as $n$ (or one less). Calculate the number of digits in $n$ and use that to determine the split point.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <cmath>

/**
 * Strategy: Square -> Multi-split check
 */
bool isKaprekar(int n) {
    if (n == 1) return true;
    
    long long sq = 1LL * n * n;
    int digits = 0;
    long long temp = sq;
    while (temp > 0) { digits++; temp /= 10; }
    
    for (int i = 1; i < digits; i++) {
        long long divisor = pow(10, i);
        long long left = sq / divisor;
        long long right = sq % divisor;
        
        // Right part cannot be zero if it's the second part
        if (right > 0 && left + right == n) return true;
    }
    return false;
}

int main() {
    int num = 297;
    if (isKaprekar(num)) std::cout << num << " is a Kaprekar number." << std::endl;
    return 0;
}
```
