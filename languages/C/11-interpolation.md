# 🟢 Standard: Interpolation (Formatting) [CORE]

## Definition
C does not have native string expansion. It uses format specifiers (placeholders like `%d`) to inject variables into strings during runtime formatting.

## 1. Legacy Way (C99 / C11 / C17)
Standard `printf` and `snprintf` workflow using Hex for bit-level visibility.

```c
#include <stdio.h>

int main() {
    int val = 12; // Binary: 1100
    char buffer[20];
    
    printf("Val: %d\n", val);          // Output: Val: 12
    printf("Hex: 0x%X\n", val);        // Output: Hex: 0xC
    
    snprintf(buffer, sizeof(buffer), "Fmt: %d", val);
    printf("%s\n", buffer);            // Output: Fmt: 12
    return 0;
}
```

## 2. Modern Way (C23)
Supports identical specifiers but works natively with C23 binary literals and `auto`.

```c
#include <stdio.h> // Required for printf

int main() {
    auto val = 0b1100; // C23 Native Binary literal (Value: 12)
    char buffer[20];
    
    printf("Val: %d\n", val);          // Output: Val: 12
    printf("Bin: 0b1100\n");           // Output: Bin: 0b1100
    
    snprintf(buffer, sizeof(buffer), "Fmt: %d", val);
    printf("%s\n", buffer);            // Output: Fmt: 12
    return 0;
}
```

# The Logic Bridge
// Logic: Formatting functions parse the string at runtime to identify `%` markers and perform the binary-to-text conversion for the specific data type.
