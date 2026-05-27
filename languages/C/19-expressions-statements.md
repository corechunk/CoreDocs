# 🟢 Standard: Expressions & Statements [CORE]

## Definition
An **Expression** is a sequence of operators and operands that reduces to a single value. A **Statement** is a complete instruction that performs an action (usually ending in `;`).

## 1. Legacy Way (C99 / C11 / C17)
Standard definition of code units.

```c
#include <stdio.h>

int main() {
    int x; // Statement
    
    x = 10 + 5; // x = 10 + 5 is an expression; the whole line is a statement.
    
    printf("Val: %d\n", x); // Output: Val: 15
    return 0;
}
```

## 2. Modern Way (C23)
Maintains the same distinction, with support for modern initializer expressions.

```c
#include <stdio.h> // Required for printf

int main() {
    // Expression: 10 + 5
    // Statement: auto x = 10 + 5;
    auto x = 10 + 5; 
    
    printf("Val: %d\n", x); // Output: Val: 15
    return 0;
}
```

# The Logic Bridge
// Logic: Expressions produce a result that can be assigned or used as input; Statements control the flow of execution and the lifecycle of data.
