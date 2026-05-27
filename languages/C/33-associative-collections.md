# 🟢 Standard: Associative Collections [CORE]

## Definition
Standard C does not have built-in Hashmaps or Dictionaries. To achieve associative mapping, developers must manually implement a Hash Table or use parallel arrays.

## 1. Legacy Way (C99 / C11 / C17)
Parallel arrays to map a Key (ID) to a Value (Score).

```c
#include <stdio.h>

int main() {
    int keys[] = {101, 102};
    int values[] = {95, 88};

    // Mirror Task: Find value for key 102
    for (int i = 0; i < 2; i++) {
        if (keys[i] == 102) {
            printf("Val: %d\n", values[i]); // Output: Val: 88
        }
    }
    return 0;
}
```

## 2. Modern Way (C23)
C23 adds `constexpr` and `auto`, which can be used to make lookup tables more robust and type-safe at compile-time.

```c
#include <stdio.h> // Required for printf

int main() {
    // Modern approach: Type-safe lookup table
    constexpr int keys[] = {101, 102};
    constexpr int values[] = {95, 88};

    for (auto i = 0; i < 2; i++) {
        if (keys[i] == 102) {
            printf("Val: %d\n", values[i]); // Output: Val: 88
        }
    }
    return 0;
}
```

# The Logic Bridge
// Logic: Without a built-in library, "Associative" behavior is simulated by mapping a computed index (Hash) to a specific memory slot in an array.
