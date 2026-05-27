# 44 | Happy Number

Check if a number eventually reaches 1 when replaced by the sum of squares of its digits.

---

## 1. The Objective
1. Square each digit and sum them.
2. Repeat the process with the new sum.
3. If you reach **1**, it's a **Happy Number**.
4. If it enters a loop (cycle) that never reaches 1, it's **Unhappy**.

- **Example:** $19$
- $1^2 + 9^2 = 82$
- $8^2 + 2^2 = 68$
- $6^2 + 8^2 = 100$
- $1^2 + 0^2 + 0^2 = 1$. (Happy!)

---

## 2. Visual Logic
### The Cycle Trap
If a number is unhappy, it always falls into the cycle: `4, 16, 37, 58, 89, 145, 42, 20, 4...`
If you see any of these numbers, stop.

---

## 3. The "Aha!" Moment
Use a `set` (or a hardcoded list of cycle numbers) to detect if you are repeating yourself. If you see the same number twice and it's not 1, you are in an infinite loop.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <unordered_set>

int sumSqDigits(int n) {
    int sum = 0;
    while (n > 0) {
        int d = n % 10;
        sum += (d * d);
        n /= 10;
    }
    return sum;
}

/**
 * Strategy: Cycle Detection
 */
bool isHappy(int n) {
    std::unordered_set<int> seen;
    
    while (n != 1 && seen.find(n) == seen.end()) {
        seen.insert(n);
        n = sumSqDigits(n);
    }
    
    return n == 1;
}

int main() {
    int num = 19;
    if (isHappy(num)) std::cout << num << " is a Happy number!" << std::endl;
    return 0;
}
```
