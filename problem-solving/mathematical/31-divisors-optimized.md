# 31 | Divisors Optimized

Find all divisors of a number in $O(\sqrt{n})$ time.

---

## 1. The Objective
Given `n = 36`, return `1, 2, 3, 4, 6, 9, 12, 18, 36`.
The naive approach (1 to $n$) is $O(n)$. We want the faster $O(\sqrt{n})$ way.

---

## 2. Visual Logic
### The "Mirror" Strategy
Divisors always come in pairs.
- $36 / 1 = 36$. (Pair: 1, 36)
- $36 / 2 = 18$. (Pair: 2, 18)
- $36 / 3 = 12$. (Pair: 3, 12)
- $36 / 4 = 9$.  (Pair: 4, 9)
- $36 / 6 = 6$.  (Pair: 6)

Once you reach $\sqrt{36}$ (which is 6), you have found all unique divisors.

---

## 3. The "Aha!" Moment
Iterate from 1 up to $\sqrt{n}$. For every $i$ that divides $n$, you get **two** divisors: $i$ and $n/i$. 
**Edge Case:** If $i \times i == n$, only count it once (to avoid duplicates like 6, 6).

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

/**
 * Strategy: O(sqrt n) Divisor Search
 */
void printDivisors(int n) {
    std::vector<int> divisors;
    
    for (int i = 1; i * i <= n; i++) {
        if (n % i == 0) {
            divisors.push_back(i);
            
            // Add the paired divisor if it's different
            if (i * i != n) {
                divisors.push_back(n / i);
            }
        }
    }
    
    // Sort for clean output
    std::sort(divisors.begin(), divisors.end());
    
    std::cout << "Divisors of " << n << ": ";
    for (int d : divisors) std::cout << d << " ";
    std::cout << std::endl;
}

int main() {
    printDivisors(36);
    return 0;
}
```
