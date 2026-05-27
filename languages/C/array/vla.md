# 🔴 Standard: Variable Length Arrays (VLA) [SYSTEMS]

## Definition
VLAs allow array sizes to be determined at runtime. Note: C11 made VLAs optional, so they should be used with caution in portable systems code.

## 1. Legacy Way (C99 / C11 / C17)
VLA declaration using a variable for size.

```c
#include <stdio.h>

void create_vla(int n) {
    int arr[n]; // Size determined at runtime
    arr[0] = 10;
    printf("VLA 0: %d\n", arr[0]); // Output: VLA 0: 10
}

int main() {
    create_vla(5);
    return 0;
}
```

## 2. Modern Way (C23)
Mirroring the same runtime-size task.

```c
#include <stdio.h>

void create_vla(int n) {
    int arr[n]; 
    arr[0] = 10;
    printf("VLA 0: %d\n", arr[0]); // Output: VLA 0: 10
}

int main() {
    create_vla(5);
    return 0;
}
```

# The Logic Bridge
// Logic: VLAs are allocated on the Stack using a dynamic stack-pointer adjustment (similar to `alloca`). This is faster than Heap allocation but can cause crashes if the runtime size is too large.
