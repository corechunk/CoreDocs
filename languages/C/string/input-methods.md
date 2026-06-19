# 🔵 Standard: String Input Methods [PRO]

## Definition
String Input Methods manage parsing and writing user characters into string buffers. Using secure bounds boundaries prevents stack buffer exploits.

## 1. Legacy Way (C99)
Legacy C inputs utilized raw `scanf` or the standard `gets()` function. Because `gets()` has no parameters for size boundaries, it continues writing input data indefinitely, leading to critical stack overflow exploits.

```c
#include <stdio.h>

int main() {
    char buf[5];
    
    // CRITICAL DANGER: Obsolete and deleted from standard C
    // gets(buf); 
    return 0;
}
```

## 2. Modern Way (C23 / C11)
Modern standards restrict inputs to bounded fields using explicitly sized `scanf` specifiers or safe stream functions like `fgets()`.

```c
#include <stdio.h>

int main() {
    char buf[6];
    
    // 1. Safe Bounded scanf (reads maximum 5 chars + writes '\0')
    printf("Enter text: ");
    scanf("%5s", buf);
    printf("Scanf: %s\n", buf);
    
    // Consume newline left in input buffer
    int c; while ((c = getchar()) != '\n' && c != EOF);

    // 2. Safe fgets (reads maximum 5 chars, always null-terminates)
    printf("Enter line: ");
    fgets(buf, sizeof(buf), stdin);
    printf("fgets: %s\n", buf);
    return 0;
}
```

## Deep-Dive Reference
* **The `gets()` Hazard**: The `gets()` function reads lines from standard input until it hits a newline character, without verifying boundary sizes. It was deprecated in C99 and completely removed from standard C in C11.
* **Bounded `scanf("%Ns", buf)`**: By inserting a number between `%` and `s`, you define a strict parsing limit. To prevent overflow in `char buf[SIZE]`, the width limit must be at most `SIZE - 1` to reserve space for the trailing null byte (`\0`).
* **`fgets(buf, size, stream)`**: Safely reads up to `size - 1` characters, stopping early if a newline (`\n`) is read. The newline is preserved inside the buffer, and a null terminator is always appended.

# The Logic Bridge
// Logic: If input limits are omitted, the standard I/O engine writes excess characters past the boundary of local stack arrays. This overrides adjacent stack variables, including the function's return instruction address (EIP/RIP), allowing arbitrary code execution exploits.
