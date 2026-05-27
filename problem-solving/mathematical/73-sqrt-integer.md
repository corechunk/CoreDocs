# 73 | Square Root (Integer)

Calculate the integer part of the square root of $n$.

---

## 1. The Objective
Given `24`, return `4` (since $\sqrt{24} \approx 4.89$).
**Constraint:** Do not use `sqrt()`.

---

## 2. Visual Logic
### The "Binary Search" Strategy
The square root of $n$ must be between 1 and $n/2$.
1. Pick `mid = (1 + 24) / 2 = 12`.
2. $12^2 = 144$ (Too high!). New range: 1 to 11.
3. Pick `mid = (1 + 11) / 2 = 6`.
4. $6^2 = 36$ (Too high!). New range: 1 to 5.
5. Pick `mid = (1 + 5) / 2 = 3`.
6. $3^2 = 9$ (Too low). New range: 4 to 5.
7. Pick `mid = 4`. $4^2 = 16$ (Too low, but next is $5^2=25$). 
Result: **4**.

---

## 3. The "Aha!" Moment
Finding a square root is essentially "searching" for a number. Binary search makes this $O(\log n)$ instead of $O(\sqrt{n})$ for a linear search.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Binary Search for Root
 * Efficiency: Time O(log n)
 */
int integerSqrt(int n) {
    if (n < 2) return n;
    
    int low = 1, high = n / 2;
    int ans = 1;
    
    while (low <= high) {
        long long mid = low + (high - low) / 2;
        if (mid * mid == n) return mid;
        
        if (mid * mid < n) {
            ans = mid;
            low = mid + 1;
        } else {
            high = mid - 1;
        }
    }
    return ans;
}

int main() {
    std::cout << "Integer sqrt of 24: " << integerSqrt(24) << std::endl;
    return 0;
}
```
