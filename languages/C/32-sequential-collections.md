# 🟢 Standard: Sequential Collections [CORE]

## Definition
Sequential collections in C are primary implemented as **Arrays**—contiguous blocks of memory storing elements of the same type. This hub covers fixed-size arrays and the evolution toward Variable Length Arrays (VLA).

## 1. Legacy Way (C99 / C11 / C17)
Standard array declaration and initialization.

```c
#include <stdio.h>

int main() {
    // Fixed-size array
    int scores[3] = {90, 80, 70};
    
    printf("Item 0: %d\n", scores[0]); // Output: Item 0: 90
    printf("Item 2: %d\n", scores[2]); // Output: Item 2: 70
    return 0;
}
```

## 2. Modern Way (C23)
Maintains same syntax, but highlights C23's support for more flexible initialization and `auto` for pointer-based iteration.

```c
#include <stdio.h> // Required for printf

int main() {
    // Mirror: Standard array task
    int scores[3] = {90, 80, 70};

    // auto: Native keyword (deduces int*)
    for (auto i = 0; i < 3; i++) {
        printf("Score %d: %d\n", i, scores[i]);
    }
    // Output: Score 0: 90
    // Output: Score 1: 80
    // Output: Score 2: 70
    return 0;
}
```

## Deep-Dive Reference
For memory layouts, VLAs, and multi-dimensional matrices:
- [Fixed-Size Arrays](./array/fixed.md) | [Variable Length Arrays (VLA)](./array/vla.md) | [Multi-Dimensional](./array/multidim.md)

# The Logic Bridge
// Logic: An array name acts as a constant pointer to the first element. Accessing `arr[i]` is identical to `*(arr + i)`, calculated by multiplying the index by the byte-size of the data type.
