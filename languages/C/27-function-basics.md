# 🟢 Standard: Function Basics [CORE]

## Definition
Functions are reusable blocks of code that perform a specific task. They take inputs (parameters) and return an output. In C, functions must be declared before use.

## 1. Legacy Way (C99 / C11 / C17)
Standard declaration with explicit return types and parameter lists.

```c
#include <stdio.h>

// Declaration (Prototype)
int add(int a, int b);

int main() {
    int result = add(5, 3);
    printf("Result: %d\n", result); // Output: Result: 8
    return 0;
}

// Definition
int add(int a, int b) {
    return a + b;
}
```

## 2. Modern Way (C23)
C23 introduces `auto` for return type inference, allowing the compiler to deduce the return type from the `return` statement.

```c
#include <stdio.h> // Required for printf

// C23: auto return type inference
auto add(int a, int b) {
    return a + b; // Compiler deduces 'int'
}

int main() {
    auto result = add(5, 3);
    printf("Result: %d\n", result); // Output: Result: 8
    return 0;
}
```

# The Logic Bridge
// Logic: A function call triggers the CPU to save the current instruction address to the "Stack" (the return address), jump to the function's memory location, and then jump back once the task is finished.
