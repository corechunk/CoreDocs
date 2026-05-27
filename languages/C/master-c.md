# 🏛️ Master C Reference: The Core Foundation

**Purpose:** A high-density, one-shot reference for the foundational logic of the C language. This file mirrors the evolution from established standards (C99/C11/C17) to the modern **C23** standard.

---

## Toolchain Installation [01]

### Definition
The environment setup required to transform source code into machine-executable binary.

### 1. Legacy Way (System-Wide)
```bash
# Arch Linux
sudo pacman -S base-devel
# Debian/Ubuntu
sudo apt update && sudo apt install build-essential

# Verify
gcc --version // Output: gcc (GCC) 13.x.x
```

### 2. Modern Way (Mise)
```bash
# Lock version per project
mise use gcc@13.2.0
export CC=gcc

# Verify
gcc --version // Output: gcc (GCC) 13.2.0
```

# The Logic Bridge
// Logic: Version locking prevents "Silent Breaking" by ensuring consistent compiler behavior across all development environments.

---

## Compilation Ritual [02]

### Definition
The command sequence to transform code into a process.

### 1. Legacy Way (Standard)
```bash
gcc -std=c99 main.c -o app
./app # Output: (Program Result)
```

### 2. Modern Way (Strict C23)
```bash
gcc -std=c23 -Wall -Wextra -Werror -Wpedantic main.c -o app
./app // Output: (Program Result)
```

# The Logic Bridge
// Logic: Strict flags move runtime risks into compile-time errors, hardening the application logic during the build phase.

---

## Tokens & Lexemes [04]

### Definition
The atomic units of C (Keywords, Identifiers, Literals).

### 1. Legacy Way (Explicit)
```c
#include <stdio.h>
int main() {
    int age = 25; // Tokens: [int] [age] [=] [25] [;]
    printf("Age: %d\n", age); // Output: Age: 25
    return 0;
}
```

### 2. Modern Way (Inferred)
```c
#include <stdio.h>
int main() {
    auto age = 25; // Tokens: [auto] [age] [=] [25] [;]
    printf("Age: %d\n", age); // Output: Age: 25
    return 0;
}
```

# The Logic Bridge
// Logic: The Lexer organizes raw text into a stream of categorized tokens for the compiler to analyze logically.

---

## Keywords & Standards [05]

### Definition
The reserved vocabulary of the language.

### 1. Legacy Way (Library-Based)
```c
#include <stdio.h>
#include <stdbool.h> // REQUIRED for C99-C17
int main() {
    bool active = true;
    printf("Active: %d\n", active); // Output: Active: 1
    return 0;
}
```

### 2. Modern Way (Native C23)
```c
#include <stdio.h>
int main() {
    bool active = true; // Native keyword
    printf("Active: %d\n", active); // Output: Active: 1
    return 0;
}
```

# The Logic Bridge
// Logic: Native keywords allow the compiler to optimize logic directly rather than relying on preprocessor macro swaps.

---

## Variables & Constants [08]

### Definition
Mutable storage vs. Immutable values.

### 1. Legacy Way (#define)
```c
#include <stdio.h>
#define MAX 100
int main() {
    const int buffer = 512;
    printf("Max: %d, Buf: %d\n", MAX, buffer); // Output: Max: 100, Buf: 512
    return 0;
}
```

### 2. Modern Way (constexpr)
```c
#include <stdio.h>
int main() {
    constexpr int MAX = 100; // Native C23
    const int buffer = 512;
    printf("Max: %d, Buf: %d\n", MAX, buffer); // Output: Max: 100, Buf: 512
    return 0;
}
```

# The Logic Bridge
// Logic: `constexpr` provides type-safe, compile-time constants that are more robust than simple preprocessor text replacement.

---

## Data Types [09]

### Definition
Defining the bit-width and interpretation of memory.

### 1. Legacy Way (Headers)
```c
#include <stdio.h>
#include <stdbool.h>
int main() {
    int i = 10; char c = 'A'; bool b = true;
    printf("Int: %d, Bool: %d\n", i, b); // Output: Int: 10, Bool: 1
    return 0;
}
```

### 2. Modern Way (Native)
```c
#include <stdio.h>
int main() {
    auto i = 10; bool b = true; // Native
    printf("Int: %d, Bool: %d\n", i, b); // Output: Int: 10, Bool: 1
    return 0;
}
```

# The Logic Bridge
// Logic: C23 simplifies the environment by moving the most fundamental types directly into the language core.

---

## String Escaping [10]

### Definition
Representing "invisible" or protected characters.

### 1. Legacy Way (ASCII)
```c
#include <stdio.h>
int main() {
    printf("NL: \nHex: \x41\n"); // Output: NL: (newline) Hex: A
    return 0;
}
```

### 2. Modern Way (Unicode)
```c
#include <stdio.h>
int main() {
    printf("Emoji: \U0001F680\n"); // Output: Emoji: 🚀
    return 0;
}
```

# The Logic Bridge
// Logic: Escape sequences insert specific byte values into the final binary's data segment.

---

## Interpolation (Formatting) [11]

### Definition
Injecting variables into strings at runtime.

### 1. Legacy Way (Standard)
```c
#include <stdio.h>
int main() {
    int val = 12;
    printf("Val: %d, Hex: 0x%X\n", val, val); // Output: Val: 12, Hex: 0xC
    return 0;
}
```

### 2. Modern Way (Binary)
```c
#include <stdio.h>
int main() {
    auto val = 0b1100; // Binary literal
    printf("Val: %d, Bin: 0b1100\n", val); // Output: Val: 12, Bin: 0b1100
    return 0;
}
```

# The Logic Bridge
// Logic: Format specifiers tell the `printf` engine how to convert binary memory into human-readable ASCII text.

---

## Scope & Lifetime [12]

### Definition
Visibility of names vs. Persistence of memory.

### 1. Legacy Way (Manual)
```c
#include <stdio.h>
int main() {
    for (int i = 0; i < 1; i++) {
        int x = 10;
        printf("X: %d\n", x); // Output: X: 10
    }
    // x is out of scope here
    return 0;
}
```

### 2. Modern Way (Auto)
```c
#include <stdio.h>
int main() {
    for (auto i = 0; i < 1; i++) {
        auto x = 10;
        printf("X: %d\n", x); // Output: X: 10
    }
    return 0;
}
```

# The Logic Bridge
// Logic: Local variables exist on the Stack; exiting a block reclaims that memory by moving the stack pointer.

---

## Operators [17]

### Definition
Symbols for Math, Logic, and Bitwise manipulation.

### 1. Legacy Way (Symbolic)
```c
#include <stdio.h>
int main() {
    int a = 10, b = 3;
    printf("Sum: %d, And: %d\n", a+b, a&b); // Output: Sum: 13, And: 2
    return 0;
}
```

### 2. Modern Way (Native Bool)
```c
#include <stdio.h>
int main() {
    auto a = 10, b = 3;
    printf("Sum: %d, And: %d\n", a+b, a&b); // Output: Sum: 13, And: 2
    return 0;
}
```

# The Logic Bridge
// Logic: Operators map directly to ALU instructions in the CPU.

---

## Conditionals [23]

### Definition
Branching execution based on logic.

### 1. Legacy Way (If/Switch)
```c
#include <stdio.h>
int main() {
    int x = 1;
    if (x == 1) printf("One\n"); // Output: One
    return 0;
}
```

### 2. Modern Way (Auto-Switch)
```c
#include <stdio.h>
int main() {
    auto x = 1;
    switch(x) { case 1: printf("One\n"); } // Output: One
    return 0;
}
```

# The Logic Bridge
// Logic: If-else is sequential; Switch is optimized into a high-speed Jump Table.

---

## Function Engine [27]

### Definition
Reusable logic blocks with inputs/outputs.

### 1. Legacy Way (Explicit)
```c
#include <stdio.h>
int add(int a, int b) { return a + b; }
int main() {
    printf("%d\n", add(5, 5)); // Output: 10
    return 0;
}
```

### 2. Modern Way (Auto Return)
```c
#include <stdio.h>
auto add(int a, int b) { return a + b; }
int main() {
    printf("%d\n", add(5, 5)); // Output: 10
    return 0;
}
```

# The Logic Bridge
// Logic: Function calls save the return address on the Stack and jump to the function's memory offset.

---

## Arrays [32]

### Definition
Contiguous memory blocks for same-type elements.

### 1. Legacy Way (Fixed)
```c
#include <stdio.h>
int main() {
    int arr[2] = {10, 20};
    printf("%d\n", arr[1]); // Output: 20
    return 0;
}
```

### 2. Modern Way (Auto Iteration)
```c
#include <stdio.h>
int main() {
    int arr[2] = {10, 20};
    for (auto i = 0; i < 2; i++) printf("%d ", arr[i]); // Output: 10 20
    return 0;
}
```

# The Logic Bridge
// Logic: `arr[i]` is a shortcut for `*(arr + i)`, calculated using the type's byte size.

---

## Structs [34]

### Definition
Custom types grouping different variables.

### 1. Legacy Way (Standard)
```c
#include <stdio.h>
struct User { int id; };
int main() {
    struct User u = {101};
    printf("ID: %d\n", u.id); // Output: ID: 101
    return 0;
}
```

### 2. Modern Way (Designated)
```c
#include <stdio.h>
struct User { int id; };
int main() {
    auto u = (struct User){ .id = 101 }; // Designated initializer
    printf("ID: %d\n", u.id); // Output: ID: 101
    return 0;
}
```

# The Logic Bridge
// Logic: A struct is a single memory block; members are accessed via pre-calculated offsets.

---

## I/O Streams [45]

### Definition
Kernel-provided paths for input and output.

### 1. Legacy Way (Standard)
```c
#include <stdio.h>
int main() {
    fprintf(stdout, "OK\n"); // Output: OK
    return 0;
}
```

### 2. Modern Way (Mirrored)
```c
#include <stdio.h>
int main() {
    fprintf(stdout, "OK\n"); // Output: OK
    return 0;
}
```

# The Logic Bridge
// Logic: `stdout` (1) and `stderr` (2) are the process's primary communication channels to the terminal or OS.

---

## Error Handling [49]

### Definition
Signaling failure via return codes and `errno`.

### 1. Legacy Way (Manual)
```c
#include <stdio.h>
#include <errno.h>
int main() {
    FILE* f = fopen("none.txt", "r");
    if (f == NULL) printf("Err: %d\n", errno); // Output: Err: 2
    return 0;
}
```

### 2. Modern Way (nullptr)
```c
#include <stdio.h>
#include <errno.h>
int main() {
    auto f = fopen("none.txt", "r");
    if (f == nullptr) printf("Err: %d\n", errno); // Output: Err: 2
    return 0;
}
```

# The Logic Bridge
// Logic: Library functions return sentinel values (like NULL) to trigger an error-check on the thread-local `errno` variable.
