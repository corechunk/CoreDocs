# 🟢 Standard: Keywords & Standards [CORE]

## Definition
Keywords are the reserved vocabulary that form the language grammar. Standards define how this vocabulary has expanded through architectural versions.

## 1. Legacy Way (C99 / C11 / C17)
Standards where Boolean logic required external library definitions.

**Evolution Snapshot:**
- C89 -> 32 Keywords (int, char, struct...)
- C99 -> 37 Keywords (Added: _Bool, inline, restrict...)
- C11 -> 44 Keywords (Added: _Atomic, _Generic, _Static_assert...)

```c
#include <stdio.h>
#include <stdbool.h> // REQUIRED for bool, true, false (C99-C17)

int main() {
    bool active = true;
    printf("Active: %d\n", active); // Output: Active: 1
    return 0;
}
```

## 2. Modern Way (C23)
Vocabulary expanded to 53 keywords, moving common logic into the language core.

**C23 Additions:**
- bool, true, false (Native)
- nullptr, constexpr, typeof, alignof

```c
#include <stdio.h> // Required for printf

int main() {
    // Native Keywords: NO header required
    bool active = true; 
    
    printf("Active: %d\n", active); // Output: Active: 1
    return 0;
}
```

# The Logic Bridge
// Logic: Native keywords (like bool in C23) allow the compiler to perform type-checking and optimization more efficiently than preprocessor macros in headers.
