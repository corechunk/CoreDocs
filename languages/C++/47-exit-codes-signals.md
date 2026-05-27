# 🔴 Standard: Exit Codes & Signals [SYSTEMS]

## Definition
Process lifecycle management and interrupt handling.

## 1. Legacy Way (C++11 / C++17)
Standard exit and signal.

```cpp
#include <iostream>
#include <csignal>
#include <cstdlib>

void handle(int sig) { std::cout << "Sig\n"; }

int main() {
    std::signal(SIGINT, handle);
    std::cout << "Run\n"; // Output: Run
    return EXIT_SUCCESS;
}
```

## 2. Modern Way (C23)
Mirroring task with `[[noreturn]]` attribute for exit functions.

```cpp
#include <iostream>
#include <csignal>
#include <cstdlib>

[[noreturn]] void quit() { std::exit(0); }

int main() {
    std::signal(SIGINT, [](int){ std::cout << "Sig\n"; });
    std::cout << "Run\n"; // Output: Run
    return EXIT_SUCCESS;
}
```

# The Logic Bridge
// Logic: Signals are processed by the OS Kernel. When a signal arrives, the Kernel pauses the process and forces it to execute the handler function on a special Signal Stack.
