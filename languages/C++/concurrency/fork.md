# 🔴 Standard: Process Forking [SYSTEMS]

## Definition
Cloning a process.

## 1. Legacy Way (C++11 / C++17)
```cpp
#include <iostream>
#include <unistd.h>

int main() {
    if (fork() == 0) std::cout << "C\n"; // Output: C
    else std::cout << "P\n"; // Output: P
    return 0;
}
```

## 2. Modern Way (C23)
```cpp
#include <iostream>
#include <unistd.h>

int main() {
    auto pid = fork();
    if (pid == 0) std::cout << "C\n"; // Output: C
    else std::cout << "P\n"; // Output: P
    return 0;
}
```

# The Logic Bridge
// Logic: `fork()` returns 0 to the child and the child's PID to the parent, allowing logic to split based on the return value.
