# 🔵 Standard: Pattern Matching [PRO]

## Definition
Pattern matching in C involves searching for specific sequences of characters within a string. This ranges from simple substring searches to full Regular Expressions via the POSIX `regex.h` library.

## 1. Legacy Way (C99 / C11 / C17)
Using `strstr` for simple literal matching or manual loops for basic patterns.

```c
#include <stdio.h>
#include <string.h>

int main() {
    const char* text = "System ID: 12345";
    const char* pattern = "ID";
    
    // Simple substring match
    char* match = strstr(text, pattern);
    
    if (match) {
        printf("Pattern Found: %s\n", match); 
        // Output: Pattern Found: ID: 12345
    }
    return 0;
}
```

## 2. Modern Way (C23)
While C23 doesn't add native regex syntax, the "Modern Pro" path uses the POSIX `regcomp` engine to perform complex logic that `strstr` cannot handle.

```c
#include <stdio.h>
#include <regex.h> // POSIX standard library

int main() {
    const char* text = "System ID: 12345";
    regex_t regex;
    
    // Compile pattern: [0-9]+ (one or more digits)
    regcomp(&regex, "[0-9]+", REG_EXTENDED);
    
    // Execute match
    int result = regexec(&regex, text, 0, NULL, 0);
    
    if (result == 0) {
        printf("Pattern Found: Digits\n"); // Output: Pattern Found: Digits
    }
    
    regfree(&regex);
    return 0;
}
```

# The Logic Bridge
// Logic: Simple matching (`strstr`) is a linear byte-comparison. Regex (`regcomp`) builds a Finite Automaton (a state machine) to evaluate complex logical patterns across the string.
