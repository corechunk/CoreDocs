# 60 | Hamming Numbers (Smooth Numbers)

Find numbers whose only prime factors are 2, 3, and 5.

---

## 1. The Objective
Also known as **Ugly Numbers** (Problem 43), but this time we want to **generate** the sequence in order:
`1, 2, 3, 4, 5, 6, 8, 9, 10, 12, 15, ...`

---

## 2. Visual Logic
### The "Triple Pointer" Strategy
Every Hamming number is $2 \times$ (prev Hamming number), $3 \times$ (prev), or $5 \times$ (prev).
- Start with `[1]`.
- Multipliers: $1 \times 2 = 2, 1 \times 3 = 3, 1 \times 5 = 5$.
- Smallest is **2**. Add to list.
- Next multipliers: $2 \times 2 = 4, 1 \times 3 = 3, 1 \times 5 = 5$.
- Smallest is **3**. Add to list.

---

## 3. The "Aha!" Moment
Instead of checking every number (slow), keep three pointers (`i2, i3, i5`) tracking which previous Hamming number you are multiplying by. This is $O(n)$ time.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

/**
 * Strategy: Triple-Pointer DP
 * Efficiency: Time O(n), Space O(n)
 */
void printHammingNumbers(int n) {
    std::vector<long long> hamming(n);
    hamming[0] = 1;
    
    int i2 = 0, i3 = 0, i5 = 0;
    long long next2 = 2, next3 = 3, next5 = 5;
    
    std::cout << "First " << n << " Hamming numbers: ";
    std::cout << hamming[0] << " ";

    for (int i = 1; i < n; i++) {
        long long nextVal = std::min({next2, next3, next5});
        hamming[i] = nextVal;
        std::cout << nextVal << " ";
        
        if (nextVal == next2) { i2++; next2 = hamming[i2] * 2; }
        if (nextVal == next3) { i3++; next3 = hamming[i3] * 3; }
        if (nextVal == next5) { i5++; next5 = hamming[i5] * 5; }
    }
    std::cout << std::endl;
}

int main() {
    printHammingNumbers(15);
    return 0;
}
```
