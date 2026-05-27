# 🔴 Standard: Multi-Dimensional Arrays [SYSTEMS]

## Definition
Multi-dimensional arrays represent grids or matrices. They are stored in "Row-Major" order—meaning they are actually a single flat line in memory.

## 1. Legacy Way (C99 / C11 / C17)
Standard 2D array syntax.

```c
#include <stdio.h>

int main() {
    int matrix[2][2] = {
        {1, 2},
        {3, 4}
    };
    
    printf("Item [1][0]: %d\n", matrix[1][0]); // Output: Item [1][0]: 3
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring the same matrix task with clearer initialization.

```c
#include <stdio.h>

int main() {
    int matrix[2][2] = {
        [0] = {1, 2},
        [1] = {3, 4}
    };
    
    printf("Item [1][0]: %d\n", matrix[1][0]); // Output: Item [1][0]: 3
    return 0;
}
```

# The Logic Bridge
// Logic: The compiler calculates the address for `[i][j]` using the formula: `BaseAddress + (i * RowSize + j) * ElementSize`.
