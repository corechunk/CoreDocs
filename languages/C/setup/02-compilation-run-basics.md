# 🟢 Standard: Compilation & Run Ritual [CORE]

## Definition
The specific command sequence used to transform human-readable code into an executable process. C23 encourages using strict standard enforcement by default.

## 1. Legacy Way (C99 / C11 / C17)
Basic compilation using standard flags to produce an output binary.

```bash
# Standard compilation using C99
gcc -std=c99 main.c -o app

# Run
./app # Output: (Result of code)
```

## 2. Modern Way (C23)
Mirroring the same task but with maximum strictness and diagnostic tools enabled to catch errors during the build phase.

```bash
# Mirror: Compiling same task with C23 and hard-mode diagnostics
gcc -std=c23 -Wall -Wextra -Werror -Wpedantic main.c -o app

# -Wall: Common warnings
# -Werror: Treat warnings as errors
# -Wpedantic: Reject non-standard extensions

# Run
./app # Output: (Result of code)
```

# The Logic Bridge
// Logic: The `-std` flag determines the "Grammar Rules" the compiler uses; modern standards (C23) provide better safety and more powerful keywords.
