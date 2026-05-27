# 23 | Primes in a Range

Print all prime numbers between two limits $L$ and $R$.

---

## 1. The Objective
Given `start = 10` and `end = 50`, print all primes in between.

---

## 2. Visual Logic
### The "Sieve-like" Filter
1. Start at `L`.
2. Check if the current number is prime (using optimized check from Problem 22).
3. If YES, print it.
4. Move to the next number.

---

## 3. The "Aha!" Moment
Reuse your `isPrime()` function inside a simple `for` loop. This is the modular way to build software—solving a big problem by using a solution for a smaller one.

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
 * Strategy: Range Iteration
 */
void printPrimesInRange(int L, int R) {
    std::cout << "Primes between " << L << " and " << R << ":" << std::endl;
    for (int i = L; i <= R; i++) {
        if (isPrime(i)) {
            std::cout << i << " ";
        }
    }
    std::cout << std::endl;
}

int main() {
    printPrimesInRange(10, 50);
    return 0;
}
```
