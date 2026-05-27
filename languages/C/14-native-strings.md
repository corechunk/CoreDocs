# 🔵 Standard: Native Strings [PRO]

## Definition
Strings in C are not objects; they are null-terminated character arrays (`char[]`). The `string.h` library provides the standard engine for copying, measuring, and comparing these arrays.

## 1. Legacy Way (C99 / C11 / C17)
Manual manipulation or standard functions like `strcpy`. Standardized since C89.

```c
#include <stdio.h>
#include <string.h>

int main() {
    char source[] = "C-String";
    char dest[20];
    
    // Copying logic
    strcpy(dest, source); 
    
    // Measuring logic
    size_t len = strlen(dest);
    
    printf("String: %s\n", dest); // Output: String: C-String
    printf("Length: %zu\n", len);  // Output: Length: 8
    return 0;
}
```

## 2. Modern Way (C23)
C23 formalizes common extensions like `strdup` and `strndup` into the standard, making heap-based string duplication cleaner.

```c
#include <stdio.h>
#include <string.h>
#include <stdlib.h> // Required for free()

int main() {
    char source[] = "C-String";
    
    // strdup: Native C23 function (allocates memory automatically)
    // Same task as strcpy but handles memory allocation
    char* dest = strdup(source); 
    
    size_t len = strlen(dest);
    
    printf("String: %s\n", dest); // Output: String: C-String
    printf("Length: %zu\n", len);  // Output: Length: 8
    
    free(dest); // Must free memory allocated by strdup
    return 0;
}
```

# The Logic Bridge
// Logic: A C-string is a sequence of bytes ending in a null byte (`\0`). Functions like `strlen` simply count bytes until they hit that zero, while `strdup` calculates the size, calls `malloc`, and copies the bytes in one step.
