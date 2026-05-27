# 🔵 Standard: Multi-File Projects [PRO]

## Definition
Scaling C applications requires splitting code into **Header Files** (`.h` for declarations) and **Source Files** (`.c` for implementation). This prevents massive files and allows for separate compilation.

## 1. Legacy Way (C99 / C11 / C17)
Using manual **Include Guards** to prevent multiple definitions if a header is included twice.

```c
// --- math_utils.h ---
#ifndef MATH_UTILS_H
#define MATH_UTILS_H

int add(int a, int b);

#endif

// --- math_utils.c ---
#include "math_utils.h"
int add(int a, int b) { return a + b; }

// --- main.c ---
#include <stdio.h>
#include "math_utils.h"

int main() {
    printf("Sum: %d\n", add(10, 5)); // Output: Sum: 15
    return 0;
}
```

## 2. Modern Way (C23)
While include guards are still standard, modern organization often uses `#pragma once` (a universally supported extension) and C23 native keywords in the interface.

```c
// --- math_utils.h ---
#pragma once // Modern, cleaner alternative to guards

auto add(int a, int b); // C23 auto in declaration

// --- math_utils.c ---
#include "math_utils.h"
auto add(int a, int b) { return a + b; }

// --- main.c ---
#include <stdio.h>
#include "math_utils.h"

int main() {
    printf("Sum: %d\n", add(10, 5)); // Output: Sum: 15
    return 0;
}
```

# The Logic Bridge
// Logic: The Preprocessor physically pastes the content of the `.h` file into the `.c` file before the compiler runs. Include guards ensure that if `A.h` is included by `B.h` and `C.h`, the compiler only sees the declarations in `A.h` once.
