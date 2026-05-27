# 🟢 Standard: Return Types [CORE]

## Definition
The Return Type defines the data type a function sends back to its caller. `void` is a special type used when a function returns nothing. Early returns are used to exit a function before reaching the end.

## 1. Legacy Way (C99 / C11 / C17)
Explicit types and `void` for actions without data return.

```c
#include <stdio.h>

void check_limit(int val) {
    if (val > 100) {
        printf("Over limit\n"); // Output: Over limit
        return; // Early return
    }
    printf("Safe\n");
}

int main() {
    check_limit(150);
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring the early return task using `auto` and modern keywords.

```c
#include <stdio.h> // Required for printf

// auto cannot be used for void functions, so we stay explicit
void check_limit(int val) {
    if (val > 100) {
        printf("Over limit\n"); // Output: Over limit
        return; 
    }
    printf("Safe\n");
}

int main() {
    auto value = 150;
    check_limit(value);
    return 0;
}
```

# The Logic Bridge
// Logic: When a function returns, the result is typically placed in a specific CPU register (like `EAX/RAX` on x86) for the caller to retrieve.
