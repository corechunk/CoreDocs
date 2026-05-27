# 🟢 Standard: Mathematical Operators [CORE]

## Definition
Symbols used to perform arithmetic on numeric values.

## 1. Legacy Way (C99 / C11 / C17)
Standard operators: `+`, `-`, `*`, `/`, `%`.

```c
#include <stdio.h>

int main() {
    int a = 10, b = 3;
    
    printf("Sum: %d\n", a + b);  // Output: Sum: 13
    printf("Div: %d\n", a / b);  // Output: Div: 3 (Integer division)
    printf("Mod: %d\n", a % b);  // Output: Mod: 1
    return 0;
}
```

## 2. Modern Way (C23)
Identical operators, mirroring the same arithmetic tasks.

```c
#include <stdio.h> // Required for printf

int main() {
    auto a = 10, b = 3;
    
    printf("Sum: %d\n", a + b);  // Output: Sum: 13
    printf("Div: %d\n", a / b);  // Output: Div: 3
    printf("Mod: %d\n", a % b);  // Output: Mod: 1
    return 0;
}
```

# The Logic Bridge
// Logic: The compiler translates these symbols into direct ALU (Arithmetic Logic Unit) instructions like `ADD`, `IDIV`, and `SUB`.
