# 🟢 Standard: Compilation Ritual [CORE]

## Definition
The sequence of commands used to transform `.cpp` source files into a runnable binary. Modern C++ (C++23) encourages stricter standard compliance.

## 1. Legacy Way (C++11 / C++17)
Basic compilation with version-specific flags.

```bash
# Standard compilation using C++11
g++ -std=c++11 main.cpp -o app

# Run
./app # Output: (Program Result)
```

## 2. Modern Way (C++23)
Strict C++23 enforcement with high-signal diagnostics.

```bash
# Mirror: Compiling same task with modern strictness
g++ -std=c++23 -Wall -Wextra -Werror -Wpedantic main.cpp -o app

# Run
./app # Output: (Program Result)
```

# The Logic Bridge
// Logic: The `-std` flag tells the compiler's frontend which set of grammar rules and standard library features to enable during the parsing stage.
