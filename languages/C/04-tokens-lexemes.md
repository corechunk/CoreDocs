# 🟢 Standard: Tokens & Lexemes [CORE]

## Definition
Tokens are the atomic units of C (Keywords, Identifiers, Operators). Lexemes are the actual text sequences. This mirror shows how a basic statement is broken down.

## 1. Legacy Way (C99 / C11 / C17)
Identifying tokens in a standard declaration.

```c
#include <stdio.h>

int main() {
    int age = 25; // Tokens: [keyword:int] [id:age] [op:=] [lit:25] [punc:;]
    
    printf("Age: %d\n", age); // Output: Age: 25
    return 0;
}
```

## 2. Modern Way (C23)
Identifying tokens involving modern keywords and type inference.

```c
#include <stdio.h> // Required for printf

int main() {
    // auto: New token category (Keyword)
    auto age = 25; // Tokens: [keyword:auto] [id:age] [op:=] [lit:25] [punc:;]
    
    printf("Age: %d\n", age); // Output: Age: 25
    return 0;
}
```

# The Logic Bridge
// Logic: Whitespace is ignored between tokens, allowing C to be a "Free-form" language where logic is grouped by punctuation rather than indentation.
