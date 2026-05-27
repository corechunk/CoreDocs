# 🔵 Standard: Closures & Lambdas [PRO]

## Definition
Standard C does not have native "Lambdas" or "Closures" (functions that capture scope). Instead, it uses **Function Pointers** to pass functions as arguments to other functions (Callbacks).

## 1. Legacy Way (C99 / C11 / C17)
Using function pointers with the `NULL` macro.

```c
#include <stdio.h>

void greet() { printf("Hello\n"); }

void executor(void (*f)()) {
    if (f != NULL) f(); // Output: Hello
}

int main() {
    executor(greet);
    return 0;
}
```

## 2. Modern Way (C23)
Using function pointers with `nullptr` and C23's stricter empty parameter list `()` which now means `(void)`.

```c
#include <stdio.h> // Required for printf

void greet() { printf("Hello\n"); }

// C23: () is now explicitly the same as (void)
void executor(void (*f)()) {
    if (f != nullptr) f(); // Output: Hello
}

int main() {
    executor(greet);
    return 0;
}
```

# The Logic Bridge
// Logic: A Function Pointer stores the memory address of the function's entry point in the "Text Segment" of the program's binary. Calling the pointer is a direct jump to that address.
