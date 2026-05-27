# 🔴 Standard: Program Execution [SYSTEMS]

## Definition
Replacing the current process image.

## 1. Legacy Way (C++11 / C++17)
Using `execl`.

```cpp
#include <iostream>
#include <unistd.h>

int main() {
    execl("/bin/echo", "echo", "Hi", NULL);
    return 0;
}
```

## 2. Modern Way (C23)
Using `nullptr`.

```cpp
#include <iostream>
#include <unistd.h>

int main() {
    execl("/bin/echo", "echo", "Hi", nullptr);
    return 0;
}
```

# The Logic Bridge
// Logic: `exec` wipes the current process memory (stack, heap, data) and loads the new binary's sections into the same PID.
