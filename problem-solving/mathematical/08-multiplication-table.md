# 08 | Multiplication Table

Generate the multiplication table for a given number $n$.

---

## 1. The Objective
Print the table from $n \times 1$ up to $n \times 10$ (or any limit).

---

## 2. Visual Logic
### Tracing (n=5)
```text
5 * 1  = 5
5 * 2  = 10
5 * 3  = 15
...
5 * 10 = 50
```

---

## 3. The "Aha!" Moment
This is the simplest use case for a `for` loop. The number `n` stays constant, while the multiplier `i` increments.

---

<br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br><br>

## 4. C++ Implementation

```cpp
#include <iostream>
#include <iomanip> // for std::setw (formatting)

/**
 * Simple Multiplication Table
 */
void printTable(int n, int limit = 10) {
    std::cout << "Multiplication Table for " << n << ":" << std::endl;
    for (int i = 1; i <= limit; i++) {
        std::cout << n << " x " << std::setw(2) << i << " = " << (n * i) << std::endl;
    }
}

int main() {
    int num;
    std::cout << "Enter a number: ";
    std::cin >> num;
    
    printTable(num);
    
    return 0;
}
```
