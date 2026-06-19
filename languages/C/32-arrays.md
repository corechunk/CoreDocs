# 🟢 Standard: Arrays [CORE]

## Definition
Arrays are contiguous memory blocks storing elements of the same type. This hub covers standard compile-time bounds, modern compiler optimizations, runtime dynamic arrays, and metadata decay mechanics.

## 1. Legacy Way (C99 / C11 / C17)
* Standard declaration specifies size at compile-time using constant literals.
* Array indexing relies on direct calculations against a base pointer.

```c
#include <stdio.h>

int main() {
    int scores[3] = {90, 80, 70};
    
    printf("Item 0: %d\n", scores[0]); // Output: 90
    printf("Item 2: %d\n", scores[2]); // Output: 70
    return 0;
}
```

## 2. Modern Way (C23)
* Standard sizes can be cleanly calculated using type-safe constant expressions (`constexpr`).
* Iteration can be performed using native `auto` type deduction for pointers.

```c
#include <stdio.h>

int main() {
    constexpr int SIZE = 3;
    int scores[SIZE] = {90, 80, 70};

    for (auto i = 0; i < SIZE; i++) {
        printf("Score %d: %d\n", i, scores[i]);
    }
    return 0;
}
```

## Deep-Dive Reference
For memory layouts, VLAs, multi-dimensional matrices, and decay behavior:
- [Fixed-Size Arrays](./array/fixed.md) | [Variable Length Arrays (VLA)](./array/vla.md) | [Multi-Dimensional](./array/multidim.md) | [Pointer Decay](./array/pointer-decay.md)

# The Logic Bridge
// Logic: An array name acts as a constant pointer to the first element. Accessing `arr[i]` compiles down to pointer offset dereferencing `*(arr + i)`.
