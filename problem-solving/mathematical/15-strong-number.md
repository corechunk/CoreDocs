# 15 | Strong Number

Check if the sum of factorials of digits equals the number itself.

---

## 1. The Objective
A number is **Strong** if $n = \text{digit}_1! + \text{digit}_2! + \dots$
- **Example:** $145 = 1! + 4! + 5! = 1 + 24 + 120 = 145$.

---

## 2. Visual Logic
### Tracing 145
1. `1! = 1`
2. `4! = 24`
3. `5! = 120`
4. `Sum = 1 + 24 + 120 = 145`
5. `145 == 145 -> YES`

---

## 3. The "Aha!" Moment
This problem combines **Digit Extraction** with **Factorial Calculation** (Problem 02). You can use a helper function for factorial to keep the code clean.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Helper: Factorial
 */
unsigned long long factorial(int n) {
    unsigned long long res = 1;
    for (int i = 2; i <= n; i++) res *= i;
    return res;
}

/**
 * Strategy: Digit Extraction + Factorial Sum
 */
bool isStrong(int n) {
    int original = n;
    unsigned long long sum = 0;
    
    while (n > 0) {
        sum += factorial(n % 10);
        n /= 10;
    }
    
    return original == sum;
}

int main() {
    int num = 145;
    
    if (isStrong(num)) {
        std::cout << num << " is a Strong number." << std::endl;
    } else {
        std::cout << num << " is NOT a Strong number." << std::endl;
    }
    
    return 0;
}
```
