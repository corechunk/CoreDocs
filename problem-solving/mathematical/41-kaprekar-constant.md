# 41 | Kaprekar Constant (6174)

The mysterious behavior of 4-digit numbers.

---

## 1. The Objective
Take any 4-digit number (at least two different digits).
1. Arrange digits in descending order.
2. Arrange digits in ascending order.
3. Subtract the smaller from the larger.
4. Repeat. You will always hit **6174** in 7 steps or less.

---

## 2. Visual Logic
### Tracing 3524
1. Desc: 5432, Asc: 2345. Diff: $5432 - 2345 = 3087$.
2. Desc: 8730, Asc: 0378. Diff: $8730 - 0378 = 8352$.
3. Desc: 8532, Asc: 2358. Diff: $8532 - 2358 = 6174$.
4. **Target Reached!**

---

## 3. The "Aha!" Moment
This problem requires **Digit Extraction**, **Sorting**, and **Iteration**. You must treat "0" as a digit to maintain 4 digits (e.g., "0378").

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
#include <cmath>

/**
 * Strategy: Sort and Subtract Loop
 */
void kaprekarRoutine(int n) {
    std::cout << "Starting with: " << n << std::endl;
    
    while (n != 6174 && n != 0) {
        std::vector<int> digits;
        int temp = n;
        for(int i=0; i<4; i++) {
            digits.push_back(temp % 10);
            temp /= 10;
        }
        
        std::sort(digits.begin(), digits.end());
        int asc = 0, desc = 0;
        for(int i=0; i<4; i++) {
            asc = asc * 10 + digits[i];
            desc = desc * 10 + digits[3-i];
        }
        
        n = desc - asc;
        std::cout << desc << " - " << asc << " = " << n << std::endl;
    }
}

int main() {
    kaprekarRoutine(3524);
    return 0;
}
```
