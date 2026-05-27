# 🔵 Standard: Jump Statements [PRO]

## Definition
Jump statements interrupt the normal sequential flow of code to skip iterations, break loops, or move to a specific labeled point.

## 1. Legacy Way (C99 / C11 / C17)
Standard keywords: `break`, `continue`, `goto`.

```c
#include <stdio.h>

int main() {
    for (int i = 0; i < 10; i++) {
        if (i == 1) continue; // Skip 1
        if (i == 3) break;    // Exit at 3
        printf("Num: %d\n", i);
    }
    // Output: Num: 0
    // Output: Num: 2
    
    goto end;
    printf("Hidden\n");
    
    end:
    printf("Done\n"); // Output: Done
    return 0;
}
```

## 2. Modern Way (C23)
Identical syntax, mirrored task. `goto` is still rarely used but exists for complex error cleanup.

```c
#include <stdio.h> // Required for printf

int main() {
    for (auto i = 0; i < 10; i++) {
        if (i == 1) continue; 
        if (i == 3) break;    
        printf("Num: %d\n", (int)i);
    }
    // Output: Num: 0
    // Output: Num: 2
    
    goto end;
    printf("Hidden\n");
    
    end:
    printf("Done\n"); // Output: Done
    return 0;
}
```

# The Logic Bridge
// Logic: `break` and `continue` are restricted jumps that only work within loop scopes. `goto` is a raw branch to a memory address (labeled), which can make code hard to read if overused.
