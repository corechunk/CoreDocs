# 24 | Nth Prime Number

Find the value of the $n^{th}$ prime number.

---

## 1. The Objective
Given `n = 5`, return `11` (Primes are 2, 3, 5, 7, **11**).

---

## 2. Visual Logic
### The "Counter" Strategy
1. Initialize `count = 0`.
2. Start checking numbers from 2 onwards.
3. Every time you find a prime, increment `count`.
4. Stop when `count == n`.

---

## 3. The "Aha!" Moment
Since we don't know exactly where the $n^{th}$ prime will be, we use a `while` loop that runs until our counter hits $n$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

bool isPrime(int n) {
    if (n <= 1) return false;
    if (n <= 3) return true;
    if (n % 2 == 0 || n % 3 == 0) return false;
    for (int i = 5; i * i <= n; i += 6) {
        if (n % i == 0 || n % (i + 2) == 0) return false;
    }
    return true;
}

/**
 * Strategy: Incremental Search
 */
int findNthPrime(int n) {
    int count = 0;
    int num = 2;
    while (true) {
        if (isPrime(num)) {
            count++;
            if (count == n) return num;
        }
        num++;
    }
}

int main() {
    int n = 100;
    std::cout << "The " << n << "th prime is: " << findNthPrime(n) << std::endl;
    return 0;
}
```
