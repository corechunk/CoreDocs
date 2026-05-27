# 🔵 Standard: Command Substitution [PRO]

## Definition
Running system commands and capturing output. C++ relies on the OS API (POSIX or Windows).

## 1. Legacy Way (C++11 / C++17)
Using `std::system`.

```cpp
#include <iostream>
#include <cstdlib>

int main() {
    int res = std::system("echo Hello"); // Output: Hello
    std::cout << "Res: " << res << "\n"; // Output: Res: 0
    return 0;
}
```

## 2. Modern Way (C23)
Capturing output via pipes (OS dependent).

```cpp
#include <iostream>
#include <cstdio>

int main() {
    char buffer[128];
    FILE* pipe = popen("echo Hello", "r");
    if (pipe) {
        fgets(buffer, sizeof(buffer), pipe);
        std::cout << buffer; // Output: Hello
        pclose(pipe);
    }
    return 0;
}
```

# The Logic Bridge
// Logic: `std::system` forks a child process. It is a "Blocking" call that waits for the OS shell to return a status code.
