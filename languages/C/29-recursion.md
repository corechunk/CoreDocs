# 🟢 Standard: Recursion [CORE]

## Definition
Recursion is when a function calls itself to solve a smaller version of the same problem. Every recursive function must have a **Base Case** to stop the execution and prevent an infinite loop.

## 1. Legacy Way (C99 / C11 / C17)
Standard recursive implementation for factorial calculation.

```c
#include <stdio.h>

long factorial(int n) {
    if (n <= 1) return 1; // Base Case
    return n * factorial(n - 1); // Recursive Step
}

int main() {
    printf("Fact: %ld\n", factorial(5)); // Output: Fact: 120
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring the same factorial task using modern type inference.

```c
#include <stdio.h> // Required for printf

auto factorial(int n) {
    if (n <= 1) return 1L; // Base Case (1L ensures 'long')
    return n * factorial(n - 1); 
}

int main() {
    auto result = factorial(5);
    printf("Fact: %ld\n", result); // Output: Fact: 120
    return 0;
}
```

# The Logic Bridge
// Logic: Each recursive call adds a new "Frame" to the Stack memory. If the recursion is too deep without hitting a base case, the Stack overflows (Stack Overflow), causing the program to crash.
