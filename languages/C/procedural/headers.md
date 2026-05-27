# Header Architecture (PRO)

Definition: Separating code into **Declarations** (`.h` files) and **Definitions** (`.c` files). This is the foundation of modularity in C.

## 1. Legacy Way (C99 / C11 / C17)
Standard header guards.

```c
// In utils.h
#ifndef UTILS_H
#define UTILS_H

void process(int data);

#endif
```

## 2. Modern Way (C23)
Using `#pragma once` (widely supported) and C23 improvements.

```c
// In utils.h
#pragma once

/**
 * Modern declaration with attributes
 */
[[nodiscard]] int calculate(int x);
```

# The Logic Bridge
// Logic: Headers allow multiple files to share the same interface without duplicating code. The compiler uses the header to verify function signatures, while the Linker later joins the actual implementation from the compiled `.o` (object) files into the final binary.
