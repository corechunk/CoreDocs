# 🟢 Standard: Passing Mechanisms [CORE]

## Definition
C uses **Pass-by-Value** by default, meaning a function receives a copy of the data. To modify the original variable, we pass its memory address (**Pass-by-Pointer**).

## 1. Legacy Way (C99 / C11 / C17)
Mirroring the task of incrementing a value using both methods.

```c
#include <stdio.h>

void inc_value(int x) { x++; }      // Value (Copy)
void inc_ptr(int* x) { (*x)++; }    // Pointer (Address)

int main() {
    int a = 10, b = 10;
    
    inc_value(a);
    inc_ptr(&b);
    
    printf("Value: %d, Ptr: %d\n", a, b); 
    // Output: Value: 10, Ptr: 11
    return 0;
}
```

## 2. Modern Way (C23)
Identical logic, mirroring the task while using `nullptr` for address safety.

```c
#include <stdio.h> // Required for printf

void inc_value(int x) { x++; }
void inc_ptr(int* x) { 
    if (x != nullptr) (*x)++; // C23 nullptr check
}

int main() {
    auto a = 10, b = 10;
    
    inc_value(a);
    inc_ptr(&b);
    
    printf("Value: %d, Ptr: %d\n", a, b); 
    // Output: Value: 10, Ptr: 11
    return 0;
}
```

# The Logic Bridge
// Logic: Pass-by-Value copies the data into the function's stack frame; Pass-by-Pointer only copies the 8-byte address, allowing the function to reach back into the caller's memory.
