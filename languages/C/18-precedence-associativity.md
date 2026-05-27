# 🟢 Standard: Order of Operations [CORE]

## Definition
Precedence determines which operator is evaluated first. Associativity determines the direction (left-to-right or right-to-left) when operators have the same precedence.

## 1. Legacy Way (C99 / C11 / C17)
Standard PEMDAS-style rules apply.

```c
#include <stdio.h>

int main() {
    // Multiplicative higher than Additive
    int result = 5 + 2 * 10; 
    
    // Assignment is Right-to-Left
    int x, y;
    x = y = 50; 

    printf("Result: %d\n", result); // Output: Result: 25
    printf("X: %d, Y: %d\n", x, y); // Output: X: 50, Y: 50
    return 0;
}
```

## 2. Modern Way (C23)
The rules of precedence are fundamental and unchanged in C23.

```c
#include <stdio.h> // Required for printf

int main() {
    // Multiplicative higher than Additive
    auto result = 5 + 2 * 10; 
    
    // Assignment is Right-to-Left
    int x, y;
    x = y = 50; 

    printf("Result: %d\n", (int)result); // Output: Result: 25
    printf("X: %d, Y: %d\n", x, y);      // Output: X: 50, Y: 50
    return 0;
}
```

# The Logic Bridge
// Logic: Precedence is handled by the Parser. It builds the syntax tree so that higher precedence nodes are deeper (evaluated first) or grouped according to associativity.
