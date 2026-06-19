# 🔵 Standard: String Declarations [PRO]

## Definition
Strings in C can be declared as Stack Arrays, Read-Only Literals, or Dynamic Heap structures. Each declaration type defines how the compiler allocates and writes memory space.

## 1. Legacy Way (C99 / C11)
Standard string allocations compile down to fixed Stack arrays or Read-Only text sections:

```c
#include <stdio.h>

int main() {
    // 1. Stack Array: Readable & Writeable
    char stack_str[] = "Hello"; 
    
    // 2. Read-Only Literal: Points directly to ROM text segment
    char *literal_str = "Hello";
    
    printf("Stack: %s, Literal: %s\n", stack_str, literal_str);
    return 0;
}
```

## 2. Modern Way (C23 / C11)
Using dynamic pointers, the system requests allocations on the Heap, rendering the memory writeable but requiring active memory tracking.

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main() {
    // Heap Pointer: Allocating mutable memory dynamically
    char *heap_str = malloc(10 * sizeof(char));
    
    if (heap_str != NULL) {
        strcpy(heap_str, "Modern"); // Safe heap write
        printf("Heap string: %s\n", heap_str);
        
        free(heap_str); // REQUIRED: release allocated memory block
    }
    return 0;
}
```

## Deep-Dive Reference
### Memory Layout Comparison
* **Stack Array (`char arr[] = "XYZ"`)**:
  - The literal `"XYZ"` is copied into mutable stack frames during function initialization.
  - The program fully owns this memory. It is **Read-Write**.
* **Literal Pointer (`char *ptr = "XYZ"`)**:
  - The compiler stores `"XYZ"` inside the binary's text/data segment (ROM).
  - The pointer `ptr` points directly to this protected location. It is **Read-Only**.
* **Heap Pointer (`char *ptr = malloc(...)`)**:
  - The system allocates anonymous raw memory cells in heap storage during execution.
  - The memory space is fully **Read-Write**.

# The Logic Bridge
// Logic: Stack arrays and Heap blocks are allocated in writeable memory pages. Literal pointers point to pages in the executable image flagged by the OS as read-only; attempts to write to these pages trigger hardware page faults.
