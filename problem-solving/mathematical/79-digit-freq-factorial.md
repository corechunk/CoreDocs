# 79 | Digit Frequency in Factorial

Count how many times each digit appears in $n!$.

---

## 1. The Objective
For small $n$, calculate $n!$ and count the occurrences of 0-9.

---

## 2. Visual Logic
### The "Array Counter"
1. Calculate Factorial.
2. Use an array `freq[10]` initialized to 0.
3. Extract each digit and `freq[digit]++`.

---

## 3. The "Aha!" Moment
Because factorials grow so large, standard `long long` only works up to $20!$. For larger $n$, you must use a **BigInt** (storing digits in an array) or a library. Here, we demonstrate the standard range.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

/**
 * Strategy: Factorial -> Digit Extraction Loop
 */
void printDigitFrequency(int n) {
    unsigned long long fact = 1;
    for (int i = 2; i <= n; i++) fact *= i;
    
    std::vector<int> freq(10, 0);
    unsigned long long temp = fact;
    
    std::cout << n << "! = " << fact << std::endl;
    
    while (temp > 0) {
        freq[temp % 10]++;
        temp /= 10;
    }
    
    for (int i = 0; i < 10; i++) {
        if (freq[i] > 0) {
            std::cout << "Digit " << i << ": " << freq[i] << " times" << std::endl;
        }
    }
}

int main() {
    printDigitFrequency(15);
    return 0;
}
```
