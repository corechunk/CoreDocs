# 77 | Modular Exponentiation

Calculate $(a^b) \pmod m$ without overflow.

---

## 1. The Objective
Calculate very large powers and take the modulo.
- **Problem:** $2^{100}$ is too large to store in any variable.
- **Solution:** Apply modulo at every step of multiplication.

---

## 2. Visual Logic
### The Modulo Property
$(x \times y) \pmod m = [(x \pmod m) \times (y \pmod m)] \pmod m$
This means we can keep the numbers small throughout the entire "Fast Power" process.

---

## 3. The "Aha!" Moment
Integrate the `% m` operation into the Binary Exponentiation loop. This is the core algorithm for RSA encryption and competitive programming.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy: Fast Power with Modulo
 */
long long modularPow(long long base, long long exp, long long mod) {
    long long res = 1;
    base %= mod; // Handle base > mod
    
    while (exp > 0) {
        if (exp % 2 == 1) res = (res * base) % mod;
        base = (base * base) % mod;
        exp /= 2;
    }
    return res;
}

int main() {
    // (5^13) % 7
    std::cout << "Result: " << modularPow(5, 13, 7) << std::endl;
    return 0;
}
```
