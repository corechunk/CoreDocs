# 36 | Emirp Number

Check if a prime number is an Emirp.

---

## 1. The Objective
An **Emirp** (prime spelled backwards) is a prime number that results in a different prime number when its digits are reversed.
- **Example:** $13$ is prime, and $31$ is also prime. (Emirp!)
- **Example:** $17$ is prime, and $71$ is also prime. (Emirp!)
- **Note:** Palindromic primes like $131$ are NOT emirps (because the reversed number is not "different").

---

## 2. Visual Logic
### The Triple-Check Strategy
1. Is $n$ prime?
2. Reverse the digits of $n$.
3. Is the reverse different from $n$?
4. Is the reverse also prime?

If all are YES, it's an Emirp.

---

## 3. The "Aha!" Moment
This problem is a "Super-Problem" that combines:
- **Prime Check** (Problem 22)
- **Reversing a Number** (Problem 11)
- **Logical AND** of multiple conditions.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

bool isPrime(long long n) {
    if (n <= 1) return false;
    if (n <= 3) return true;
    if (n % 2 == 0 || n % 3 == 0) return false;
    for (int i = 5; i * i <= n; i += 6) {
        if (n % i == 0 || n % (i + 2) == 0) return false;
    }
    return true;
}

long long reverseNum(long long n) {
    long long rev = 0;
    while (n > 0) {
        rev = (rev * 10) + (n % 10);
        n /= 10;
    }
    return rev;
}

/**
 * Strategy: Multi-condition Primality
 */
bool isEmirp(long long n) {
    if (!isPrime(n)) return false;
    
    long long rev = reverseNum(n);
    
    // Must be different and also prime
    return (n != rev) && isPrime(rev);
}

int main() {
    int num = 13;
    if (isEmirp(num)) std::cout << num << " is an Emirp!" << std::endl;
    else std::cout << num << " is NOT an Emirp." << std::endl;
    return 0;
}
```
