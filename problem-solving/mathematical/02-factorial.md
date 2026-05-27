# 02 | Factorial

Calculate the product of all positive integers up to $n$.

---

## 1. The Objective
Factorial ($n!$) is defined as:
$n! = n \times (n-1) \times (n-2) \times \dots \times 1$
- **Note:** $0! = 1$ (by definition).

---

## 2. Visual Logic
### Tracing 5!
```text
5! = 5 * 4!
   = 5 * (4 * 3!)
   = 5 * (4 * (3 * 2!))
   = 5 * (4 * (3 * (2 * 1!)))
   = 5 * (4 * (3 * (2 * 1)))
   = 5 * 4 * 3 * 2 * 1
   = 120
```

---

## 3. The "Aha!" Moment
- **Iterative:** Start at 1 and multiply your way up. It's like a snowball rolling down a hill.
- **Recursive:** Factorial is the "purest" example of recursion. To know $n!$, you must know $(n-1)!$.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>

/**
 * Strategy A: Iterative
 * Efficiency: Time O(n), Space O(1)
 */
unsigned long long factorialIterative(int n) {
    unsigned long long result = 1;
    for (int i = 1; i <= n; i++) {
        result *= i;
    }
    return result;
}

/**
 * Strategy B: Recursive
 * Efficiency: Time O(n), Space O(n) due to recursion stack
 */
unsigned long long factorialRecursive(int n) {
    if (n <= 1) return 1;
    return n * factorialRecursive(n - 1);
}

int main() {
    int n = 5;
    
    std::cout << n << "! (Iterative): " << factorialIterative(n) << std::endl;
    std::cout << n << "! (Recursive): " << factorialRecursive(n) << std::endl;
    
    return 0;
}
```
