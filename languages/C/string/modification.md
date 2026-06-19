# 🔵 Standard: Character Modification [PRO]

## Definition
Character modification defines how individual string characters are modified at specific indexes. This behavior behaves differently depending on whether memory pages are flagged as read-write or read-only by the hardware memory management unit.

## 1. Legacy Way (C99 / C11)
Attempts to modify characters in read-only literal segments cause immediate runtime execution aborts, whereas stack array modifications run cleanly.

```c
#include <stdio.h>

int main() {
    char stack_arr[] = "Hello";
    
    // Stack Array Modification
    stack_arr[0] = 'M'; // ✅ WORKS: stack memory is read-write.
    printf("Stack modified: %s\n", stack_arr); // Output: Mello
    return 0;
}
```

## 2. Modern Way (C23 / C11)
Modifications using dynamic heap memory blocks compile and execute cleanly, providing writeable arrays whose sizes can be determined dynamically.

```c
#include <stdio.h>
#include <stdlib.h>

int main() {
    char *heap_ptr = malloc(6 * sizeof(char));
    if (heap_ptr != NULL) {
        heap_ptr[0] = 'H';
        heap_ptr[1] = 'i';
        heap_ptr[2] = '\0';
        
        // Heap Modification
        heap_ptr[0] = 'B'; // ✅ WORKS: heap pages are writeable.
        printf("Heap modified: %s\n", heap_ptr); // Output: Bi
        
        free(heap_ptr);
    }
    return 0;
}
```

## Deep-Dive Reference
### Direct Manipulation Comparison

| Operation | `char arr[]` (Stack Array) | `char *ptr` (Literal Pointer) | `char *ptr` (Heap Pointer) |
| :--- | :--- | :--- | :--- |
| **Direct Edit (`str[0] = 'M'`)**| ✅ **Works Perfectly** | ❌ **Instant Crash** *(Segfault)* | ✅ **Works Perfectly** |
| **`printf("%s", str)`** | ✅ **Works Perfectly** | ✅ **Works Perfectly** | ✅ **Works Perfectly** |
| **`fgets(str, size, stdin)`** | ✅ **Works Perfectly** | ❌ **Instant Crash** *(Segfault)* | ✅ **Works Perfectly** |
| **`strcpy(str, src)`** | ⚠️ **Buffer Overflow Risk** | ❌ **Instant Crash** *(Segfault)* | ⚠️ **Buffer Overflow Risk** |

# The Logic Bridge
// Logic: Literal pointer writes (e.g. `char *ptr = "Hello"; ptr[0] = 'M';`) compile down to write instructions targeting constant strings. The CPU's memory controller captures this write operation targeting a read-only memory page, raising a hardware exception (SIGSEGV).
