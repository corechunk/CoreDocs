# 26 | Sieve of Eratosthenes

Generate all prime numbers up to $n$ efficiently.

---

## 1. The Objective
Given `n = 20`, return all primes up to 20: `2, 3, 5, 7, 11, 13, 17, 19`.
The previous range method (Problem 23) was $O(n \sqrt{n})$. The Sieve is $O(n \log \log n)$, which is much faster for large $n$.

---

## 2. Visual Logic
### The "Elimination" Strategy
1. Create a list of all numbers from 2 to $n$.
2. Start with the first prime (2). Cross out all of its multiples (4, 6, 8...).
3. Move to the next uncrossed number (3). Cross out its multiples (6, 9, 12...).
4. Repeat until you reach $\sqrt{n}$.

```text
[2]  3  [4]  5  [6]  7  [8]  9  [10]
 11 [12] 13 [14] [15] 16 17 [18] 19 [20]
```
*(Numbers in brackets are crossed out)*

---

## 3. The "Aha!" Moment
Instead of checking if each number is prime, you **assume** they are all prime and then **eliminate** the ones that are not. This "Memory vs. Speed" trade-off is a core DSA concept.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <vector>

/**
 * Strategy: Sieve of Eratosthenes
 * Efficiency: Time O(n log log n), Space O(n)
 */
void sieve(int n) {
    // Create a boolean array "isPrime[0..n]" and initialize
    // all entries it as true. A value in isPrime[i] will
    // finally be false if i is Not a prime, else true.
    std::vector<bool> isPrime(n + 1, true);
    isPrime[0] = isPrime[1] = false;
    
    for (int p = 2; p * p <= n; p++) {
        // If isPrime[p] is not changed, then it is a prime
        if (isPrime[p]) {
            // Update all multiples of p starting from p*p
            for (int i = p * p; i <= n; i += p)
                isPrime[i] = false;
        }
    }
    
    // Print all prime numbers
    std::cout << "Primes up to " << n << ": ";
    for (int p = 2; p <= n; p++) {
        if (isPrime[p])
            std::cout << p << " ";
    }
    std::cout << std::endl;
}

int main() {
    int n = 50;
    sieve(n);
    return 0;
}
```
