# 🔴 Standard: Pointer Arithmetic [SYSTEMS]

## Definition
Pointers can be incremented or decremented to navigate through memory blocks (like arrays). The CPU calculates the move based on the byte-size of the data type.

## 1. Legacy Way (C99 / C11 / C17)
Navigating an array using pointers.

```c
#include <stdio.h>

int main() {
    int arr[] = {10, 20, 30};
    int* ptr = arr;

    printf("P1: %d\n", *ptr);     // Output: P1: 10
    ptr++;                        // Move 4 bytes (size of int)
    printf("P2: %d\n", *ptr);     // Output: P2: 20
    
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring same navigation task using `auto`.

```c
#include <stdio.h>

int main() {
    int arr[] = {10, 20, 30};
    auto ptr = arr; // auto-infers int*

    printf("P1: %d\n", *ptr);     // Output: P1: 10
    ptr++; 
    printf("P2: %d\n", *ptr);     // Output: P2: 20
    
    return 0;
}
```

# The Logic Bridge
// Logic: `ptr + 1` in C does NOT mean "plus one byte." It means "plus one unit of the type." If `ptr` is an `int*`, it jumps 4 bytes. If it's a `char*`, it jumps 1 byte.
