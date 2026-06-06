# 🔵 Standard: Standard Library [PRO]

## Definition
The C Standard Library (`libc`) is the collection of built-in functions that handle I/O, math, string manipulation, and system interaction. 

## 1. Legacy Way (C99 / C11 / C17)
Reliance on a vast array of headers for basic logic.

```c
#include <stdio.h>   // I/O
#include <string.h>  // Strings
#include <math.h>    // Math
#include <stdlib.h>  // Memory/Process

int main() {
    printf("Lib Ready\n"); // Output: Lib Ready
    return 0;
}
```

## 2. Modern Way (C23)
C23 refines the standard library by adding more utility functions and making common extensions part of the core standard.

```c
#include <stdio.h>
#include <string.h> // C23 adds new string utils
#include <stdlib.h> // C23 adds free_sized

int main() {
    // auto: Native C23
    auto msg = "Lib Ready";
    printf("%s\n", msg); // Output: Lib Ready
    return 0;
}
```

# The Logic Bridge
// Logic: The Standard Library is actually a pre-compiled binary provided by your OS (like `glibc` on Linux). When you include a header, you are only importing the "Menu" (declarations); the Linker provides the actual "Food" (implementations) from the system's shared library.

---
*See also: [Libc Implementations](../../OS/Linux/Core/Libc-Implementations.md)*

