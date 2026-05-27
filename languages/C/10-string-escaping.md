# 🟢 Standard: String Escaping [CORE]

## Definition
Escaping uses a backslash `\` to represent "invisible" characters (like newlines) or protected characters (like quotes) within a string literal.

## 1. Legacy Way (C99 / C11 / C17)
Standard ASCII-based escape sequences.

```c
#include <stdio.h>

int main() {
    printf("Line 1\nLine 2\n");   // Output: Line 1 (next line) Line 2
    printf("Hex: \x41\n");        // Output: Hex: A
    printf("Quote: \"Hi\"\n");    // Output: Quote: "Hi"
    printf("Slash: \\ \n");       // Output: Slash: \ 
    return 0;
}
```

## 2. Modern Way (C23)
Maintains legacy escapes while adding native support for Universal Unicode characters.

```c
#include <stdio.h> // Required for printf

int main() {
    // Universal Character Names (UCN)
    printf("Rocket: \U0001F680\n"); // Output: Rocket: 🚀
    
    // Classic sequences still work
    printf("Hex: \x41\n");          // Output: Hex: A
    printf("Quote: \"Hi\"\n");      // Output: Quote: "Hi"
    return 0;
}
```

# The Logic Bridge
// Logic: Escaping is a Preprocessor/Lexer instruction that replaces a two-character sequence with the actual single-byte code (e.g., ASCII 10 for `\n`) in the binary string.
