# 🔴 Standard: Pointer Decay [SYSTEMS]

## Definition
Pointer decay is the automatic conversion of an array type into a pointer to its first element when passed into a function or used in an expression. This optimization saves stack memory but strips size metadata (`sizeof` information) from the array.

## 1. Legacy Way (C99 / C11 / C17)
* When arrays are passed to functions, they implicitly decay to pointers.
* `sizeof` inside the receiving function returns the pointer size (e.g., 4 or 8 bytes) rather than the array's actual size in bytes.
* Developers must pass the size of the array as an explicit auxiliary parameter to prevent out-of-bounds reads/writes.

```c
#include <stdio.h>

// Array parameter implicitly decays to int*
void print_array_legacy(int arr[], size_t size) {
    // sizeof(arr) returns size of int* (8 bytes on 64-bit systems), NOT the array size!
    printf("Legacy fn sizeof: %zu\n", sizeof(arr)); 
    for (size_t i = 0; i < size; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

int main() {
    int my_arr[5] = {10, 20, 30, 40, 50};
    printf("Main sizeof: %zu\n", sizeof(my_arr)); // Output: 20 (5 * 4 bytes)
    print_array_legacy(my_arr, 5);
    return 0;
}
```

## 2. Modern Way (C23)
* In C23, pointer decay still occurs by default for performance, but type-safe parameters and length validations can be handled more explicitly.
* We can use parameter syntax with `static` bounds or pass a pointer to the entire array (`int (*arr)[5]`) to enforce type-checked boundaries and retain size metadata.

```c
#include <stdio.h>

// Enforces that the passed array has at least 5 elements
void print_bounded_c23(int arr[static 5]) {
    for (auto i = 0; i < 5; i++) {
        printf("%d ", arr[i]);
    }
    printf("\n");
}

// Passing pointer-to-array preserves sizeof metadata but requires explicit sizing
void print_by_array_pointer(int (*arr_ptr)[5]) {
    printf("C23 pointer-to-array sizeof: %zu\n", sizeof(*arr_ptr)); // Output: 20
    for (auto i = 0; i < 5; i++) {
        printf("%d ", (*arr_ptr)[i]);
    }
    printf("\n");
}

int main() {
    int my_arr[5] = {10, 20, 30, 40, 50};
    print_bounded_c23(my_arr);
    print_by_array_pointer(&my_arr);
    return 0;
}
```

# The Logic Bridge
// Logic: C passes arguments by value; copying whole contiguous array blocks to the stack on function calls would ruin execution performance. Decay drops the high-level bounds metadata to pass a single address reference.
