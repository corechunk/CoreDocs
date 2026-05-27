# 🔴 Standard: Charset & Encoding [SYSTEMS]

## Definition
The character map that translates binary bits into human-readable symbols. C treats characters as integers, moving from 1-byte ASCII to native Unicode support.

## 1. Legacy Way (C99 / C11 / C17)
Handling basic 1-byte characters and relying on external locale handling for multi-byte support.

```c
#include <stdio.h>

int main() {
    char a = 'A';          // ASCII 65
    char newline = '\n';   // ASCII 10 (Line Feed)
    
    printf("Char: %c, Val: %d\n", a, a); // Output: Char: A, Val: 65
    printf("NL Val: %d\n", newline);     // Output: NL Val: 10
    return 0;
}
```

## 2. Modern Way (C23)
Native support for Universal Character Names (UCN) and modern Unicode literals.

```c
#include <stdio.h> // Required for printf

int main() {
    char a = 'A';
    char newline = '\n';
    
    // C23: Universal Unicode Literals (Native Support)
    printf("Emoji: \U0001F680\n");      // Output: Emoji: 🚀
    
    printf("Char: %c, Val: %d\n", a, a); // Output: Char: A, Val: 65
    return 0;
}
```

# The Logic Bridge
// Logic: The Lexer identifies character literals and converts them to their numeric codes based on the source encoding (UTF-8) during the compilation phase.
